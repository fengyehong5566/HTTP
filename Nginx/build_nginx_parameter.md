nginx的rpm包：  
　　nginx支持动态模块,下面的模块被动态的built,并作为单独的包进行使用  
　　　　nginx-module-geoip  
　　　　nginx-module-image-filter  
　　　　nginx-module-njs  
　　　　nginx-module-perl  
　　　　nginx-module-xslt  

源码安装nginx:　　

	configure命令支持一下参数：【使用范围】　　
		--prefix=path   #指定nginx目录。
		--sbin-path=	#设置一个nginx的可执行文件的名称（此名称仅在安装过程中使用）。默认文件名为 ${prefix}/sbin/nginx
		--conf-path=	#设置一个名为nginx.conf的配置文件。如果需要的话，nginx可以用不同的配置文件启动，如：“-c file”
		--pid-path=		#设置一个名为nginx.pid的文件,用于存储主进程的进程ID【全局】

		--error-log-path=	#设置一个文件名,用于存储主错误、警告、诊断等日志
					【syntax：error_log file [level]; 
					  default：error_log logs/error.log error;】
		--http-log-path=	#设置一个文件名,用于记录http服务的请求日志
					【Syntax:	access_log path [format [buffer=size] [gzip[=level]] [flush=time] [if=condition]];
							access_log off;
					Default: access_log logs/access.log combined;
					Context: http, server, location, if in location, limit_except】

		--build=	#设置一个可选的nginx build名字
		--user=		#设置一个无特权用户,其凭据将被工作进程使用,默认nobody
		--group=	#设置一个用户组,其凭据将被工作进程使用,默认为${user}名字

		--with-select_module=	#开启/禁用模块，该模块允许服务使用select()方法工作，如果平台不发布支持更合适的方法(如:kqueue、epoll或/dev/poll),该模块将自动创建
			--without-select_module=

		--with-poll_module=		#开启/禁用模块，该模块允许服务使用poll()方法工作，如果平台不发布支持更合适的方法(如:kqueue、epoll或/dev/poll),该模块将自动创建
			--without-poll_module=

		--without-http_proxy_module=	#禁止构建http服务的代理模块
		--with-http_ssl_module=		#启用模块,该模块向http服务添加HTTPS协议的支持,默认不启用,如需构建和运行该模块,则依赖OpenSSL库

		--without-http_gzip_module=		#禁止压缩http服务的响应,如需构建和运行该模块,则依赖zlib库
		--with-zlib=	#设置zlib库的源路径,需要从zlib站点下载库分发版(版本1.1.3 1.2.11)，并提取.其他的由nginx的configure和make命令完成,该库是ngx_http_giz_modle模块所必需的

		--without-http_rewrite_module=	#禁止,该模块能让http服务进行重定向和改变请求的URI，如需构建和运行该模块,则依赖PCRL库
		--with-pcre=	#设置PCRE库的源路径,在版本(4.4-8.41)中,需要去PCRE的网站下载并安装.其他的由nginx的configure和make命令完成,该库是location指令和ngx_http_rewrite_module模块中正则表达式支持所必需的。
		--with-pcre-jit=	#使用“just-in-time(即时编译)”支持(1.1.12，pcre_jit指令)构建PCRE库。


		--with-cc-opt=	#增加CFLAGS变量的其他附加参数,当在FreeBSD下使用系统PCRE库时,应该指定'--with-cc-opt="-I /usr/local/include"',如果需要增加select()支持的文件的数量，那么也可以在这里指定，如：--with--cc-opt="-D FD_SETSIZE=2048"
		--with-ld-opt=		#设置连接期间使用的其他参数，当在FreeBSD下使用系统PCRE库时,应该指定'--with-ld-opt="-L /usr/local/lib"'
























The configure command supports the following parameters:
    >
    --help　打印帮助信息.
    --prefix=path 指定nginx安装目录，默认 /usr/local/nginx  
    --sbin-path=path 指定可执行文件的存放目录，默认 prefix/sbin/nginx  
    --modules-path=path 指定nginx动态模块的安装路径， 默认 prefix/modules  
    --conf-path=path 指定配置文件的目录及名字，默认 prefix/conf/nginx.conf  
    --error-log-path=path 设置主要错误，警告和诊断文件的名称， 默认 prefix/logs/error.log  
    --pid-path=path 设置pid文件的名字. 默认 prefix/logs/nginx.pid  
    --lock-path=path 设置锁定文件名称的前缀。默认 prefix/logs/nginx.lock (安装文件锁定，防止安装文件被别人利用，或自己误操作）  
    --user=name 设置主程序的启动用户，默认 nobody   
    --group=name 设置主程序的启动用户组， 默认 nobody  
    --build=name 设置一个可选的nginx构建名  
    --builddir=path 设置一个编译目录
      
    --with-select_module
    --without-select_module （一种轮询模式,不推荐在高载环境下使用）  
    enables or disables building a module that allows the server to work with the select() method. This module is built automatically if the platform does not appear to support more appropriate methods such as kqueue, epoll, or /dev/poll.
    
    --with-poll_module
    --without-poll_module  启用poll模块支持（功能与select相同，与select特性相同，为一种轮询模式,不推荐在高载环境下使用）
    enables or disables building a module that allows the server to work with the poll() method. This module is built automatically if the platform does not appear to support more appropriate methods such as kqueue, epoll, or /dev/poll.
    
    --with-threads  启用线程池
    
    --with-file-aio 允许在FreeBSD和Linux上使用异步文件I/O (AIO)
    
    --with-http_ssl_module 启用https协议的支持，默认不启用【依赖OpenSSL】 
    
    --with-http_v2_module 构建支持HTTP/2模块，默认不支持  
    
    --with-http_realip_module  该模块将客户端地址更改为在指定的标头字段中发送的地址。默认情况下未构建此模块  
    
    --with-http_addition_module 该模块在响应之前和之后添加文本。默认情况下不构建此模块。  
    
    --with-http_xslt_module
    --with-http_xslt_module=dynamic 该模块使用一个或多个XSLT样式表转换XML响应。默认不构建此模块。依赖libxml2和libxslt库  
    
    --with-http_image_filter_module
    --with-http_image_filter_module=dynamic  该模块可以转换JPEG，GIF，PNG和WebP格式的图像。默认不构建此模块  
    
    --with-http_geoip_module
    --with-http_geoip_module=dynamic  该模块根据客户端IP地址和预编译的MaxMind数据库创建变量。默认不构建此模块  
    
    --with-http_sub_module  该模块通过将一个指定的字符串替换为另一个指定的字符串来修改响应。默认不构建此模块  
    
    --with-http_dav_module 该模块通过WebDAV协议提供文件管理自动化。默认不构建此模块  
    
    --with-http_flv_module 该模块为Flash Video（FLV）文件提供伪流服务器端支持。默认不构建此模块  
    
    --with-http_mp4_module 该模块为MP4文件提供伪流服务器端支持。默认不构建此模块  
    
    --with-http_gunzip_module  该模块为不支持“gzip”编码方法的客户端使用“Content-Encoding: gzip”解压缩响应。默认不构建此模块  
    
    --with-http_gzip_static_module  该模块支持发送扩展名为“ .gz”的预压缩文件，而不是常规文件。默认不构建此模块
    
    --with-http_auth_request_module 该模块基于子请求的结果实现客户端授权。默认不构建此模块  
    
    --with-http_random_index_module 该模块处理以斜杠（'/'）结尾的请求，并在目录中选择一个随机文件作为索引文件。
    
    --with-http_secure_link_module 构建 ngx_http_secure_link_module 模块，默认不构建
    
    --with-http_degradation_module 构建 ngx_http_degradation_module 模块，默认不构建
    
    --with-http_slice_module 该模块将请求拆分为子请求，每个子请求返回一定范围的响应。该模块提供了更有效的大响应缓存。默认不构建
    
    --with-http_stub_status_module 该模块提供对基本状态信息的访问。默认不构建  
    
    
    ##默认禁用模块
    --without-http_charset_module 该模块将指定的字符集添加到“ Content-Type”响应标头字段中，并且可以另外将数据从一个字符集转换为另一个字符集。  
    
    --without-http_gzip_module 禁用构建可压缩HTTP服务器响应的模块。 依赖zlib库  
    
    --without-http_ssi_module 该模块在通过它的响应中处理SSI(服务器端包括)命令。  
    
    --without-http_userid_module 该模块设置适用于客户端标识的cookie。
    
    --without-http_access_module 该模块允许限制对某些客户端地址的访问。  
    
    --without-http_auth_basic_module 该模块允许通过使用“ HTTP基本身份验证”协议验证用户名和密码来限制对资源的访问。  
    
    --without-http_mirror_module 该模块通过创建后台镜像子请求来实现原始请求的镜像。  
    
    --without-http_autoindex_module 该模块处理以斜杠字符(' / ')结尾的请求，并在ngx_http_index_module模块找不到索引文件时生成目录列表。  
    
    --without-http_geo_module 该模块根据客户端IP地址创建变量值。
    
    --without-http_map_module 该模块根据其他变量的值创建变量。  
    
    --without-http_split_clients_module 该模块创建用于A / B测试的变量  
    
    --without-http_referer_module 该模块可以阻止对“ Referer”标头字段中具有无效值的请求的站点访问。  
    
    --without-http_rewrite_module 禁止构建允许HTTP服务器重定向请求和更改请求的URI的模块。依赖PCRE库。
    
    --without-http_proxy_module 禁用构建HTTP服务器代理模块  
    
    --without-http_fastcgi_module 禁用构建将请求传递到 FastCGI 服务器的模块。
    
    --without-http_uwsgi_module 禁用构建将请求传递到 uwsgi 服务器的模块。
    
    --without-http_scgi_module 禁用构建将请求传递到 SCGI 服务器的模块。
    
    --without-http_grpc_module 禁用构建将请求传递到 gRPC 服务器的模块。
    
    --without-http_memcached_module 该模块从memcached服务器获取响应.  
    
    --without-http_limit_conn_module 该模块限制每个键的连接数，例如，单个IP地址的连接数。
    
    --without-http_limit_req_module 该模块限制每个密钥的请求处理速率，例如，来自单个IP地址的请求的处理速率。
    
    --without-http_empty_gif_module 禁止构建发出单像素透明GIF的模块。
    
    --without-http_browser_module 该模块创建的变量的值取决于“User-Agent”请求头字段的值。
    
    --without-http_upstream_hash_module 禁用构建实现哈希负载平衡方法的模块。
    
    --without-http_upstream_ip_hash_module 禁用构建实现ip_hash负载平衡方法的模块。
    
    --without-http_upstream_least_conn_module 禁用构建实现 least_conn 负载平衡方法的模块  
    
    --without-http_upstream_keepalive_module 禁用构建一个模块来提供对上游服务器连接的缓存。 
    
    --without-http_upstream_zone_module 禁用构建一个模块，该模块可以将上游组的运行时状态存储在共享内存区域中。  
    
    --with-http_perl_module
    --with-http_perl_module=dynamic
    支持构建嵌入式Perl模块。默认情况下不构建此模块。
    
    --with-perl_modules_path=path 定义保存Perl模块的目录。
    
    --with-perl=path 设置Perl二进制文件的名称。
    
    --http-log-path=path 设置HTTP服务器的主请求日志文件的名称。安装后，可以使用access_log指令在nginx.conf配置文件中更改文件名。默认情况下，文件命名为prefix/logs/access.log  
    
    --http-client-body-temp-path=path
    defines a directory for storing temporary files that hold client request bodies. After installation, the directory can always be changed in the nginx.conf configuration file using the client_body_temp_path directive. By default the directory is named prefix/client_body_temp.
    
    --http-proxy-temp-path=path
    defines a directory for storing temporary files with data received from proxied servers. After installation, the directory can always be changed in the nginx.conf configuration file using the proxy_temp_path directive. By default the directory is named prefix/proxy_temp.
    
    --http-fastcgi-temp-path=path
    defines a directory for storing temporary files with data received from FastCGI servers. After installation, the directory can always be changed in the nginx.conf configuration file using the fastcgi_temp_path directive. By default the directory is named prefix/fastcgi_temp.
    
    --http-uwsgi-temp-path=path
    defines a directory for storing temporary files with data received from uwsgi servers. After installation, the directory can always be changed in the nginx.conf configuration file using the uwsgi_temp_path directive. By default the directory is named prefix/uwsgi_temp.
    
    --http-scgi-temp-path=path
    defines a directory for storing temporary files with data received from SCGI servers. After installation, the directory can always be changed in the nginx.conf configuration file using the scgi_temp_path directive. By default the directory is named prefix/scgi_temp.
    
    --without-http
    disables the HTTP server.
    
    --without-http-cache
    disables HTTP cache.
    
    --with-mail
    --with-mail=dynamic
    enables POP3/IMAP4/SMTP mail proxy server.
    
    --with-mail_ssl_module
    enables building a module that adds the SSL/TLS protocol support to the mail proxy server. This module is not built by default. The OpenSSL library is required to build and run this module.
    
    --without-mail_pop3_module
    disables the POP3 protocol in mail proxy server.
    
    --without-mail_imap_module
    disables the IMAP protocol in mail proxy server.
    
    --without-mail_smtp_module
    disables the SMTP protocol in mail proxy server.
    
    --with-stream
    --with-stream=dynamic
    enables building the stream module for generic TCP/UDP proxying and load balancing. This module is not built by default.
    
    --with-stream_ssl_module
    enables building a module that adds the SSL/TLS protocol support to the stream module. This module is not built by default. The OpenSSL library is required to build and run this module.
    
    --with-stream_realip_module
    enables building the ngx_stream_realip_module module that changes the client address to the address sent in the PROXY protocol header. This module is not built by default.
    
    --with-stream_geoip_module
    --with-stream_geoip_module=dynamic
    enables building the ngx_stream_geoip_module module that creates variables depending on the client IP address and the precompiled MaxMind databases. This module is not built by default.
    
    --with-stream_ssl_preread_module
    enables building the ngx_stream_ssl_preread_module module that allows extracting information from the ClientHello message without terminating SSL/TLS. This module is not built by default.
    
    --without-stream_limit_conn_module
    disables building the ngx_stream_limit_conn_module module that limits the number of connections per key, for example, the number of connections from a single IP address.
    
    --without-stream_access_module
    disables building the ngx_stream_access_module module that allows limiting access to certain client addresses.
    
    --without-stream_geo_module
    disables building the ngx_stream_geo_module module that creates variables with values depending on the client IP address.
    
    --without-stream_map_module
    disables building the ngx_stream_map_module module that creates variables with values depending on values of other variables.
    
    --without-stream_split_clients_module
    disables building the ngx_stream_split_clients_module module that creates variables for A/B testing.
    
    --without-stream_return_module
    disables building the ngx_stream_return_module module that sends some specified value to the client and then closes the connection.
    
    --without-stream_upstream_hash_module
    disables building a module that implements the hash load balancing method.
    
    --without-stream_upstream_least_conn_module
    disables building a module that implements the least_conn load balancing method.
    
    --without-stream_upstream_zone_module
    disables building a module that makes it possible to store run-time state of an upstream group in a shared memory zone.
    
    --with-google_perftools_module
    enables building the ngx_google_perftools_module module that enables profiling of nginx worker processes using Google Performance Tools. The module is intended for nginx developers and is not built by default.
    
    --with-cpp_test_module
    enables building the ngx_cpp_test_module module.
    
    --add-module=path
    enables an external module.
    
    --add-dynamic-module=path
    enables an external dynamic module.
    
    --with-compat
    enables dynamic modules compatibility.
    --with-cc=path
    sets the name of the C compiler.
    --with-cpp=path
    sets the name of the C preprocessor.
    --with-cc-opt=parameters
    sets additional parameters that will be added to the CFLAGS variable. When using the system PCRE library under FreeBSD, --with-cc-opt="-I /usr/local/include" should be specified. If the number of files supported by select() needs to be increased it can also be specified here such as this: --with-cc-opt="-D FD_SETSIZE=2048".
    
    --with-ld-opt=parameters
    sets additional parameters that will be used during linking. When using the system PCRE library under FreeBSD, 
    
    --with-ld-opt="-L /usr/local/lib" should be specified.
    --with-cpu-opt=cpu
    enables building per specified CPU: pentium, pentiumpro, pentium3, pentium4, athlon, opteron, sparc32, sparc64, ppc64.
    
    --without-pcre
    disables the usage of the PCRE library.
    
    --with-pcre
    forces the usage of the PCRE library.
    
    --with-pcre=path
    sets the path to the sources of the PCRE library. The library distribution (version 4.4 — 8.43) needs to be downloaded from the PCRE site and extracted. The rest is done by nginx’s ./configure and make. The library is required for regular expressions support in the location directive and for the ngx_http_rewrite_module module.
    
    --with-pcre-opt=parameters
    sets additional build options for PCRE.
    
    --with-pcre-jit
    builds the PCRE library with “just-in-time compilation” support (1.1.12, the pcre_jit directive).
    
    --with-zlib=path
    sets the path to the sources of the zlib library. The library distribution (version 1.1.3 — 1.2.11) needs to be downloaded from the zlib site and extracted. The rest is done by nginx’s ./configure and make. The library is required for the ngx_http_gzip_module module.
    
    --with-zlib-opt=parameters
    sets additional build options for zlib.
    
    --with-zlib-asm=cpu
    enables the use of the zlib assembler sources optimized for one of the specified CPUs: pentium, pentiumpro.
    
    --with-libatomic 强制使用libatomic_ops库。
    
    --with-libatomic=path
    sets the path to the libatomic_ops library sources.
    
    --with-openssl=path
    sets the path to the OpenSSL library sources.
    
    --with-openssl-opt=parameters 为OpenSSL设置其他构建选项。
    
    --with-debug 启用 debug 日志
    
    Example of parameters usage (all of this needs to be typed in one line):

>

./configure
    --sbin-path=/usr/local/nginx/nginx
    --conf-path=/usr/local/nginx/nginx.conf
    --pid-path=/usr/local/nginx/nginx.pid
    --with-http_ssl_module
    --with-pcre=../pcre-8.44
    --with-zlib=../zlib-1.2.11
After configuration, nginx is compiled and installed using make.
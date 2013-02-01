PLUGINDIR=`/usr/local/mysql/bin/mysql_config --variable=plugindir`
INCLUDE=`/usr/local/mysql/bin/mysql_config --include` -I/usr/local/include
LIBS=-lhiredis -L$(PLUGINDIR)

linux:
	gcc -Werror -O2 $(INCLUDE) -I. -fPIC -shared -rdynamic lib_mysqludf_redis.c utils.c\
		$(LIBS) -o $(PLUGINDIR)/lib_mysqludf_redis.so
		
solaris:
	gcc -DMYSQL_DYNAMIC_PLUGIN -O2 -m64 $(INCLUDE) -I. -fPIC \
		 -shared lib_mysqludf_redis.c utils.c -static-libgcc -lhiredis \
		 $(LIBS) -o $(PLUGINDIR)/lib_mysqludf_redis.so


uninstall:
	rm -f $(PLUGINDIR)/lib_mysqludf_redis.so

clean:
	rm -f *~
	rm -f *.so
	rm -f *.out

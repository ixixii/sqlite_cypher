# sqlite_cypher
对sqlite数据库加密

5 使用方法:


5.1、在工程里,拖加入sqlite3.h 和 sqlite3.c,下载地址https://github.com/ixixii/sqlite_cypher

5.2、在target –> Build Setting –> Other C Flags添加

-DSQLITE_HAS_CODEC
-DSQLITE_THREADSAFE
-DSQLCIPHER_CRYPTO_CC
-DSQLITE_TEMP_STORE=2

5.3、在target –> Build Setting –> Other Linker Flags添加

-framework Security配置

5.4、 打开FMDatabase.m,在方法
- (BOOL)openWithFlags:(int)flags vfs:(NSString *)vfsName
添加


//加密 OR 输入密码  
    const char* key = [@"beyond.2016.xsism.com" UTF8String];  
    sqlite3_key(_db, key, strlen(key)); 

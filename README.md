# JAVA_JDBC
```JAVA
package jdbc_study;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.mysql.jdbc.Driver;

public class Demo {
	public static void main(String[] args) throws ClassNotFoundException, SQLException{
		//1.注册驱动，反射技术，将驱动加入到内容
		Class.forName("com.mysql.jdbc.Driver");
		
    //2.获得数据库连接，DriverManager类中的静态方法
    //static Connection getConnection(String url,String user,String password)
    //url：数据库地址，jdbc:/mysql://连接主机IP：端口号//数据库名字
		String url = "jdbc:mysql://localhost:3306/mybase";
		String username = "root";
		String password = "123";
		Connection con =  DriverManager.getConnection(url,username,password);
	  
    //3.获得语句执行平台，通过数据库连接对象，获取到SQL语句的执行者对象
		Statement stat = con.createStatement();
		
    //4.执行sql语句
    //执行数据库中的SQL语句，int executeUpdate(String sql) insert delete update
		//只有这个步骤改变，其它步骤都是一样的
		int row = stat.executeUpdate("INSERT INTO users(uid,uname,uaddress) VALUES(1,'lisi','beijing')");
		System.out.println(row);
		
    //5.处理结果，这里没有
    
    //6.释放资源，
		stat.close();
		con.close();
		
	}
}

```

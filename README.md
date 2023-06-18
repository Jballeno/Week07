"# Week07" 
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.promineotech</groupId>
  <artifactId>mysql-javaproject7</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  
  <properties>
	  <java.version>17</java.version>
	  </properties>
  
    <dependencies>

  <dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <version>8.0.33</version>
</dependency>
</dependencies>

<build>
    <pluginManagement>
      <plugins>
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.11.0</version>
          <configuration> 
			<source>${java.version}</source>
			<target>${java.version}</target>    
          </configuration>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>

</project>


package Project7.exception;

@SuppressWarnings("serial")
public class DbException extends RuntimeException {

	public DbException() {
		// TODO Auto-generated constructor stub
	}

	public DbException(String message) {
		super(message);
		// TODO Auto-generated constructor stub
	}

	public DbException(Throwable cause) {
		super(cause);
		// TODO Auto-generated constructor stub
	}

	public DbException(String message, Throwable cause) {
		super(message, cause);
		// TODO Auto-generated constructor stub
	}

	public DbException(String message, Throwable cause, boolean enableSuppression, boolean writableStackTrace) {
		super(message, cause, enableSuppression, writableStackTrace);
		// TODO Auto-generated constructor stub
	}

}

package Project7.dao;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import Project7.exception.*;

public class DbConnection {
	
	private static final String HOST = "localhost";
	private static final String USER = "ProjectWeek7";
	private static final String PASSWORD = "ProjectWeek7";
	private static final String SCHEMA = "projectweek7";
	private static final int PORT = 3306;
	
	public static Connection getConnection() {
	//	String uri = String.format("jbdc:mysql://%s:%d/%s?user=%s&password=%s", HOST, PORT, SCHEMA, USER, PASSWORD);
	//	Connection conn = DriverManager.getConnection(uri);
	//	System.out.println("Testing the new connection");
	//	return conn;
		
		String url = String.format
				("jdbc:mysql://%s:%d/%s?user=%s&password=%s&useSSL=false", 
						HOST, PORT, SCHEMA, USER, PASSWORD);
		
		System.out.println("Connecting with url = " + url);
		
		try {
			Connection conn = DriverManager.getConnection(url);
			System.out.println("Successfully obtained connection!");
			return conn;
		} catch (SQLException e) {
			System.out.println("Error getting connection...");
			throw new DbException(e);
		}
		
		
	}
	
	

}


package Project7;

import java.sql.Connection;
import java.sql.SQLException;

import Project7.dao.DbConnection;

public class project7 {

	public static void main(String[] args) {
	Connection conn = DbConnection.getConnection();
	
		
		

	}

}




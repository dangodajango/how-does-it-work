Below are examples of how certain database operations are performed in plain JDBC versus how they can be simplified and improved using Spring JDBC.

### Executing a query

**Plain JDBC:**
```
try (Connection conn = DriverManager.getConnection(url, username, password);
     Statement stmt = conn.createStatement();
     ResultSet rs = stmt.executeQuery("SELECT * FROM users")) {

    while (rs.next()) {
        System.out.println(rs.getString("name"));
    }
} catch (SQLException e) {
    e.printStackTrace();
}

```

**Spring JDBC**

```
JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource); List<String> names = jdbcTemplate.queryForList("SELECT name FROM users", String.class); names.forEach(System.out::println);
```

### Inserting data

**Plain JDBC:**
```
try (Connection conn = DriverManager.getConnection(url, username, password);
     PreparedStatement pstmt = conn.prepareStatement("INSERT INTO users (name, email) VALUES (?, ?)")) {

    pstmt.setString(1, "John Doe");
    pstmt.setString(2, "john.doe@example.com");
    pstmt.executeUpdate();
} catch (SQLException e) {
    e.printStackTrace();
}
```

**Spring JDBC:**

```
JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
jdbcTemplate.update("INSERT INTO users (name, email) VALUES (?, ?)", "John Doe", "john.doe@example.com");

```

### Updating Data

**Plain JDBC:**
```
try (Connection conn = DriverManager.getConnection(url, username, password);
     PreparedStatement pstmt = conn.prepareStatement("UPDATE users SET email = ? WHERE name = ?")) {

    pstmt.setString(1, "new.email@example.com");
    pstmt.setString(2, "John Doe");
    pstmt.executeUpdate();
} catch (SQLException e) {
    e.printStackTrace();
}
```

**Spring JDBC:**
```
JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
jdbcTemplate.update("UPDATE users SET email = ? WHERE name = ?", "new.email@example.com", "John Doe");
```

### Handling Transactions

**Plain JDBC:**
```
try (Connection conn = DriverManager.getConnection(url, username, password)) {
    conn.setAutoCommit(false);
    try (PreparedStatement pstmt1 = conn.prepareStatement("INSERT INTO users (name, email) VALUES (?, ?)");
         PreparedStatement pstmt2 = conn.prepareStatement("UPDATE users SET email = ? WHERE name = ?")) {

        pstmt1.setString(1, "John Doe");
        pstmt1.setString(2, "john.doe@example.com");
        pstmt1.executeUpdate();

        pstmt2.setString(1, "new.email@example.com");
        pstmt2.setString(2, "John Doe");
        pstmt2.executeUpdate();

        conn.commit();
    } catch (SQLException e) {
        conn.rollback();
        throw e;
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

**Spring JDBC:**
```
JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource);
TransactionTemplate transactionTemplate = new TransactionTemplate(transactionManager);

transactionTemplate.execute(status -> {
    jdbcTemplate.update("INSERT INTO users (name, email) VALUES (?, ?)", "John Doe", "john.doe@example.com");
    jdbcTemplate.update("UPDATE users SET email = ? WHERE name = ?", "new.email@example.com", "John Doe");
    return null;
});
```
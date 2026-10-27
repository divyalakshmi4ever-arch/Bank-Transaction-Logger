BANK TRANSACTION LOGGER - SPRING AOP
Eclipse run steps (Java 17 or later)

PROJECT STRUCTURE
bank-aop/
  pom.xml
  src/main/java/demo/bankaop/BankAopApplication.java
  src/main/java/demo/bankaop/BankService.java
  src/main/java/demo/bankaop/LoggingAspect.java

BEFORE STARTING
1. Install JDK 17 or later.
2. In Eclipse, select Window > Preferences > Java > Installed JREs and select your JDK.
3. Internet connection is needed the first time Maven downloads Spring dependencies.

IMPORT INTO ECLIPSE
1. Extract bank-aop.zip to a folder you can find easily.
2. Open Eclipse.
3. Select File > Import.
4. Choose Maven > Existing Maven Projects, then click Next.
5. Browse to the extracted bank-aop folder. Select the folder containing pom.xml.
6. Ensure pom.xml is selected and click Finish.
7. Wait until Maven finishes downloading dependencies. If errors remain, right-click the project
   > Maven > Update Project... > select Force Update of Snapshots/Releases > OK.
8. In Project Explorer, expand src/main/java > demo.bankaop.
9. Right-click BankAopApplication.java > Run As > Java Application.
   If Spring Boot options appear, Run As > Spring Boot App also works.

EXPECTED CONSOLE OUTPUT
Look for messages similar to these (timestamps and ordering of framework startup lines may differ):

[AOP] Transaction started: deposit
Deposited: 1000.0, balance: 2000.0
[AOP] Transaction completed: deposit
[AOP] Transaction started: withdraw
Withdrawn: 250.0, balance: 1750.0
[AOP] Transaction completed: withdraw
[AOP] Transaction started: withdraw
[AOP] Transaction failed: withdraw - Insufficient balance
Handled error: Insufficient balance

NOTES
- This is a console demo; it does not require a database or Tomcat.
- Maven must be able to download dependencies on the first run.
- This sample demonstrates AOP logging only; it does not implement database transactions or rollbacks.

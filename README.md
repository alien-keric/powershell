# powershell
- simple modified powershell can be used to gain access from one user to another using but it needs what is know as password

assume we have managed to get a shell and we have meet something like this maybe 
```
public final class Playercounter extends JavaPlugin {  
  public void onEnable() {  
    Rcon rcon = null;  
    try {  
      rcon = new Rcon("127.0.0.1", 27015, "s67u84zKq8IXw".getBytes());  
    } catch (IOException e) {  
      throw new RuntimeException(e);  
    } catch (AuthenticationException e2) {  
      throw new RuntimeException(e2);


This issue can be referenced from a craft machine from hack the box
```

- If we try to discete the code we can see that is trying to create a playercounter plugin with a onEnable() method being enabled, with the method we can see the the is a Rcon class which tried to establish remote connection with the above port,ip and password as "s67u84zKq8IXw". first it will try to connect and if the authentication fails it throws an exceptions error and it will stop loading the plugin

- now lets see how we can abuse this into getting a shell as an adminstrator, first we will need the following credential object based parameter

# Create credential object based on parameters

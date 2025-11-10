# Algorithm for file updates in Python

## Project description

I’m a security professional working at a healthy care company. The project goes over my routine checks to identify any IP addresses that are on the `remove list` that are still on the `allow list`. Allowing me to remove any IP addresses that are no longer permitted.

## Open the file that contains the allow list

My first step is to open the file containing the allow list. 

For this step, I use the `with` statement along with the `open()` function to open the variable `import_file` which is assigned to `allow_list.txt`, the file containing the allowed IP addresses. I’m using the `r` parameter as I plan on reading the file. Which is assigned as `file` in the `with` statement.  

```
#Assign 'import_file' to the name of the file
import_file = "allow_list.txt"

#Assign 'remove_list' to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

#First line of 'with' statement
with open(import_file, "r") as file:
```

## Read the file contents

The next step is to read the file contents. I use the variable `ip_addresses` to store the imported file of the allowed list. I do this by using the `.read()` method on the `file` variable, which is assigned to `ip_addresses` to convert the contents into a string. 

I then use `print()` with `ip_addresses` as the parameter to display the `allow_list.txt` as a string.  

```
#Build 'with' statement to read the initial contents of the file
with open(import_file, "r") as file:

#Use '.read()' to read the imported file and store it in a variable name 'ip_addresses'
ip_addresses = file.read()

#Display 'ip_addresses'
print(ip_addresses)
```

## Convert the string into a list

This step is to convert the string into a list to allow me to remove the individual IP addresses from the allow list later on. I do this by using the `.split()` method on the `ip_addresses` variable, to convert the variable from a string to a list.

```
#User '.split()' to convert 'ip_addresses' from a string to a list
ip_addresses = ip.addresses.split()
```

## Iterate through the remove list

For this step, I need to use an iterative statement to loop through the `remove_list` variable to list out each IP address that needs to be removed from the `allowed_list.txt` file. This is done using the `for` loop to iterate through the `remove_list` variable with `element` being the loop variable. I use `print()` to display the IP addresses.

```
#Assign 'remove_list' to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.07.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

#Build iterative statement
#Name loop variable 'element'
#Loop through 'remove_list'

for element in remove_list:

  #Display 'element' in every iteration
  print(element)
```
<br>192.168.97.225
<br>192.168.158.170
<br>192.168.201.40
<br>192.168.58.57

## Remove IP addresses that are on the remove list

For this step, I am going to use an `if` statement as a conditional to remove any IP address found in the `remove_list` variable from the `ip_addresses` variable. I do this by using the `if` conditional that if an IP address is looped in the `element` loop variable, and matches an IP address in the `remove_list` variable, it will trigger the `.remove()` method for the `ip_addresses` variable to remove that IP address, as the `element,` from the `ip_addresses` variable. This is possible because no duplicates were found when reviewing the `ip_addresses.`

```
#Build iterative statement
#Name loop variable 'element'
#Loop through 'ip_addresses'

for element in ip_addresses:

  #Build conditional statement
  #If current element is in 'remove_list'
    If element in remove_list:

      #then current element should be removed from 'ip_addresses'
      ip_addresses.remove(element)
```

## Update the file with the revised list of IP addresses 

The last step is to update the file with the new revised list of approved IP addresses with the recently removed IP addresses. This is done by using the `.join()` method. This allows the variable to be converted back to a string to be saved into the text `allowed_list.txt` file.

I assign the `ip_addresses` variable with the following to add the list with a new line  to concatenate the list. `ip_addresses = “/n”.join(ip_addresses)`

I then make a new `with` statement using the `.write()` method to overwrite the `import_file` variable, which is assigned as the `file` variable for the `with` statement. Which updates the `allowed_list.txt` file.

```
#Convert 'ip_addresses' back to a string so that it can be written into the text file
ip_addresses = "/n".join(ip_addresses)
with open(import_file, "w") as file:
  #Rewrite the file, replacing its content with 'ip_addresses'
  file.write(ip_addresses)  
```

## Summary

I was able to update the `allowed_list.txt` file by using the `with` statement and the `open()` function to open and edit the file. I was able to use the `“r”` parameter and `.read()` method to read the file and the `“w”` parameter and `.write()` method to overwrite the file with the new list

I used the `for` loop iterative and a `if` conditional statement to remove any IP addresses found in the `remove_list` on the `allowed_list.txt`. This was done by converting the `allowed_list.txt file` into a string with `.read()`, then a list with `.split()`. Then running the `if` statement with the conditional. Once the list was updated, the list was converted back to a string with `.join()`. Then saved with the `.write()`method.  

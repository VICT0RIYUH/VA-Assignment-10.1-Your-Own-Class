**Victoria Ayala
File: va_your_own_class.py
GitHub Link: 

A description of the class. (This only needs to be a short paragraph.)
The class is called class Package. When calling the class, it takes in size (small-xlarge), the number of items in the package, its weight in lbs, 
the status, and a list of items within the package. Through the class, you can use get_size, get_items, get_status, get_weight, package_condition, 
cancel_package, cancel_item, return_package, delivery_time, reorder_package, and view_items. 

A description of each of the class and data variables.
class variables:
    packaging: Uses a string method to describe the type of packaging. Set to "cardboard box" for all.
    packaging. Uses a string method to describe the type of package protection. Set to "bubble wrap" for all.
data variables:
    self.__size: Uses the input of size to create a data variable of the package's size.
    self.__num_items: Uses the input of the number of items in the package to create a data variable of the number of items.
    self.__weight: Uses the input of the weight to create the data variable of the package's weight. 
    self.__status: Uses the inputted status to create the data variable of the package's status. 
    self.__item_list: Uses the list of items inputted to creat the data variable of the list of items in the package.

A description of each of the methods. 
get_size: This method uses the self.__size to returns itself.
get_items: This method calls return self.__num_items to return the number of items in the package.
get_status: This method first corrects the status by using title() to title case it. Then it returns the title cased status to the user.
get_weight: This method uses self.__weight to return the weight (in lbs) of the package to the user.
package_condition: This method uses the package's status to return its condition. It compares the class variable of the package protection to bubble wrap 
to ensure the protection was not changed. If the status is in transit or processing and it matches, it returns the message that it is protected. If it is a delivered status,
the message tells the user to contact the mailer is damage was done. If the package protection did not match, an unknown condition is returned.
cancel_package: The method uses the package's status to determine the if the package can be cancelled or not. A message is returned about the success of the cancellation.
cancel_item: The method takes in the argument of the item hoping to be cancelled and uses the package's status to see if changes can still be made. If the package is in transit or delivered, items can not be cancelled. If it is processing,
the method removes the item from the list and allows for the cancellation. 
return_package: The method uses the package's status to see if it is eligible for return. It returns a message of success or failure.
delivery_time: The method uses the package's status to estimate how long the package will take to arrive. It returns the range of time in days it is expected to take. 
reorder_package: The method allows for users to order packages again. It returns the package count and message of success.
view_items: The method uses the list of items to return a string of the items in the package.

Demo Program Documentation
In the demo program, three example packages are created. The lists of their items are first made and they are followed by calling the class to specify
the other properties of the package. Different methods are called but throughout each of the examples, almost all methods are used (not all get-set methods are used).
Each example uses different status to show the different functions the class has.
To run the demo program, you only have to click the Play (Run Python File) button. You may make adjustments to the demo for numbers, capitilazation, etc but the
order the arguments are inputted can not be changed in the demo. **

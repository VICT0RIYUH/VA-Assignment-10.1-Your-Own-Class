'''
Victoria Ayala
va_your_own_class.py
Assignment 10.1: Your Own Class
The program takes in information about an inputted package and processes it through class Package. The information can be used to get the package's size,
weight, number of items, and status. The pgram can also be used to get the package's condititon, try to cancel the package, try to cancel an item, try to
return the package, estimate delviery time left (in days), to reorder the package, and to view the items in the package. 
'''

class Package:
    packaging = "cardboard box"
    package_protection = "bubble wrap"
    def __init__(self, size, num_items, weight, status, item_list):
        self.__size = size          #Package is small, medium, large, or xlarge
        self.__num_items = num_items    #Number of items within the package (1 phone case + 2 chargers = 3 items)
        self.__weight = weight      #Weight (in lbs) of package
        self.__status = status.lower()      #Package is delivered, in transit, or processing
        self.__item_list = item_list  #Allows for a list of items in the package
        if status == "delivered":
            package_num = 0                     #no packages expected so number is set to 0
        elif status == "in transit" or "processing":
            package_num = 1                     #only one package expected so number is set to 1 
        self.__package_num = package_num

    def get_size(self):
        return self.__size          #returns size of package
    def get_items(self):
        return self.__num_items         #returns number of items in the package
    def get_status(self):
        status = self.__status.title()
        return status               #returns title cased package status
    def get_weight(self):
        return self.__weight        #returns weight of package (lbs)

    def package_condition(self):
        if self.__status == "delivered":            #if package was delivered, different messages are returned
            if self.package_protection == "bubble_wrap":                    #always true unless user changes class variable of package protection
                type_protection = self.package_protection.strip('"')        #removes quotes from string
                return f"Package is protected by {type_protection} and should have been delivered undamaged. If you notice any damage, please contact the mailer."
            else:
                    return f"Package protection is {self.package_protection}, condition unknown. Please contact the mailer if any damage was found upon delivery."
        if self.__status == "in transit":
            if self.package_protection == "bubble_wrap":                    #always true unless user changes class variable of package protection
                type_protection = self.package_protection.strip('"')        #removes quotes from string
                return f"Package is protected by {type_protection} and is undamaged"    #returns statement with the type of package protection as well as package's condition
            else:
                return f"Package protection is {self.package_protection}, condition unknown"    #returns type of package protection but no condition
        elif self.__status == "processing":
            return f"The package has not been created yet. Check back when status has changed." #Because the package isn't made, the condition can't be checked
    def cancel_package(self):
        self.__status = self.__status.lower()                                       #allows for comparison operators to function
        if self.__status == "delivered" or "in transit":                            
            return "Your package can only be returned by contacting the mailer."    #Does not allow package to be cancelled
        if self.__status == "processing":                       
            self.__status == "Processing for return"                                #changes status of package
            return f"Your package will be no longer be sent."                       #returns message to user that the package is no longer being sent
    def cancel_item(self, item):
        if self.__status == "processing":
            self.__item_list.remove(item)                                           #removed cancelled item if package is still processing
            cancelled_item = item.title()                                           #title case of item for display in next line 
            return f"The following will be no longer be sent in the package: {cancelled_item}"  #lets user know the item won't be sent
        elif self.__status == "delivered" or "in transit":                      #for the other statuses
            return "Your item can only be cancelled by contacting the mailer."  #item can't directly be cancelled, message is returned
    def return_package(self):                   
        self.__status = self.__status.lower()               #allows for comparison operators to function in case user inputs unusual title format
        if self.__status == "delivered":                        
            return "Please read instructions on receipt for return information."    #does not allow delivered items to be returned through program
        if self.__status == "in transit" or "processing":
            self.__status == "Processing for return"                                #changes status
            return f"Your package will be returned. Expect a refund in 5-7 business days.\nPackage Status: {self.__status.title()}" #returns two lines, one with the message of confirmation, the other with the status
    def delivery_time(self):
        if self.__status == "delivered":
            delivery_days = 0                       #no delivery time left, already delivered
            return "Your package has arrived."
        if self.__status == "in transit":
            delivery_days = 4                       #lowest estimation of delivery time for in transit package
            return f"Your package is expected to arrive in {delivery_days}-{int(delivery_days)+3} days" #provides more realistic delivery estimation by adding 3 days to value from previous line
        if self.__status == "processing":
            delivery_days = 7                       #lowest estimation of delivery time for processing package
            return f"Your package is expected to arrive in {delivery_days}-{int(delivery_days)+3} days" #provides more realistic delivery estimation by adding 3 days to value from previous line
    def reorder_package(self):
        self.__package_num += 1
        return f"Your package will be reordered. Expect {self.__package_num} packages to arrive. Await an email confirmation before accessing package information."   #lets user know how many packages will be delivered but does not let them use the program to get the new package's info
    def view_items(self):
        item_list = str(self.__item_list)
        item_list = item_list.strip("[]")
        item_list = item_list.replace("'", "")          #Format the list by converting it to a string, removing the brackets and apostrophes
        item_list = item_list.title()                   #Formats the item names for nicer display
        return f"Your package includes the following items:\n{item_list}"   #Returns a message with the items in a new line        

def main():
    '''This is the first example to demonstrate what the program can do
    The example begins by creating a list if items within the package
    It calls Package to give more information, giving the size, the number of items, the wewight in lbs, the status, and the list of items
    Line 100 calls cancel item to cancel the shoes from the order. Given the "processing" status, it should yield success and remove shoes from the list
    Then, the package items are printed to return what items are in the package following the cancellation
    Then, the package condition is printed to find out if the package is protected. Last the weight (lbs) of the package is printed. '''
    my_package_list = ["beanie", "shoelaces", "skateboard grip", "shoes", "socks"]
    my_package = Package("medium", 5, 4, "prOcessing", my_package_list)
    my_package.cancel_item("shoes")
    print(my_package.view_items())
    print(my_package.package_condition())
    print(my_package.get_weight())
    '''This is the second example and begins by creating a list of items in the package.
    It then calls package to specify the size (xlarge), number of items in the package (through length of list), the weight (in lbs) of the package, its status, and the list of items.
    Then it prints the status to reconfirm it. After, it gets the delivery time. The pacckage is reordered twice and it gets printed once to see the total number of packages to expect.'''
    your_package_list = ["Christmas_ligHts", "inflatable_decor", "candy_canes", "hot_coCoA", "santa_hat"]
    your_package = Package("xlarge", len(your_package_list), 10, "in transit", your_package_list)
    print(your_package.get_status())
    print(your_package.delivery_time())
    your_package.reorder_package()
    print(your_package.reorder_package())
    '''This is the third example to show what the program does. It creates the list of items in the package, then uses the class to specify its properties.
    Delivery time is first printed followed by trying to return and cancel the package. Because of the status of this package, neither will work. Then reorder package is called and allows for the user to expect another pacakge for every time it is called.'''
    roommate_package_list = ["speaker","bts cd", "bts photocard", "bts hoodie"]
    roomate_package = Package("small",4,3, "delivered", roommate_package_list)
    print(roomate_package.delivery_time())
    print(roomate_package.return_package())
    print(roomate_package.cancel_package())
    print(roomate_package.reorder_package())
    
if __name__ == "__main__":
    main()

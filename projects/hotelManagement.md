---
layout: project
type: project
image: img/hotel.jpg
title: "Hotel Management"
date: 2023
published: true
labels:
  - C++
  - School Project
  - Group Project
  - Teamwork
summary: "A C++ Program created by my peers and I that manages hotel rooms."
---

This C++ program implements a Hotel Management System developed by my group in ICS 212. It provides core functionalities such as managing rooms, checking customers in and out, searching for available rooms, and generating guest summaries. The program uses Room and Customer classes to handle information about hotel rooms and customer details. Key features include adding, searching, and deleting rooms, as well as verifying room availability before customer check-in. It also calculates total charges during check-out based on the room rate and number of days stayed. The program utilizes vectors to store rooms and customers, with input validation embedded throughout the check-in and check-out processes to ensure accurate data handling. Although the program had initial bugs related to phone number validation and memory allocation, these were resolved in the final update.

Here is some code that I created :

```cpp
class Customer {
  public:
    string name;
    string address;
    string phoneNumber;
    string advancePaid;
    string bookingID; 
    string checkInDate; 
    string checkOutDate;
    int roomCheckedInto;  

    Customer() {} // default contructor

    Customer(string n, string id, string addr, string phone, string ap, string checkin, string checkout) {
      name = n;
      bookingID = id;
      address = addr;
      phoneNumber = phone;
      advancePaid = ap;
      checkInDate = checkin;
      checkOutDate = checkout;
    }

    // Displays Customers details 
    void displayCustomerDetails() {
      cout << "Customer First Name: " << name << endl;
      cout << "Room Number: " << roomCheckedInto << endl;
      cout << "Address (city only): " << address << endl;
      cout << "Phone: " << phoneNumber << endl;
    }

    // setters 
    void setName(string n) { name = n; }
    void setAddress(string a) { address = a; }
    void setPhone(string p) { phoneNumber = p; }
    void setAdvancePaid(string ap) { advancePaid = ap; }
    void setRoomCheckedInto(int roomNum){roomCheckedInto = roomNum; }

    // getters 
    string getName() { return name; }
    string getAddress() { return address; }
    string getPhone() { return phoneNumber; }
    string getAdvancePaid() { return advancePaid; }
    int getRoomCheckedInto() { return roomCheckedInto; }
};
```

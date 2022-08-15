# Playing-With-Linked-List
<h3>Multiple C++ codes that perform specific tasks for linked lists</h3>


Function that takes a list of objects and returns the same list where a copy of the objects is appended at the end in reverse order.
<br>For example:
<br>input = 123456789
<br>output = 123456789987654321</br>
```
template <typename Object>
void mirrorDLL(DoubleNode<Object>*& head) {//DoubleNode refers to a double linked list
    if (head == nullptr)
        cout << "The list is empty";
    DoubleNode<Object>* node = head;
    while (node->next != nullptr)
        node = node->next;
    DoubleNode<Object>* temp = node;
    DoubleNode<Object>* newtemp = node;
    for (; temp != nullptr && newtemp != nullptr; temp = temp->prev, newtemp = newtemp->next) {
        DoubleNode<Object>* newNode = new DoubleNode<Object>{ temp->data };
        if (temp->next == nullptr) {
            temp->next = newNode;
            newNode->next = nullptr;
            newNode->prev = temp;
        }
        else {
            newtemp->next = newNode;
            newNode->next = nullptr;
            newNode->prev = newtemp;
        } 
    }
}
```

Function that returns true if the value passed is found in the list passed as arguments
```
template <typename Object>
bool findInSLL(SingleNode<Object>* head, Object value) {//SingleNode refer to a single linked list
    for (SingleNode* temp = head; temp != nullptr; temp = temp->next ) {
        if (temp->data == value) 
            return true;
    return false;
}
```
Funtion that finds a given value and inserts a new node with the new value passed as argument after it. 
<br>Returns true if the insertion is successful, else false.</br>
```
template <typename Object>
bool insertAfterSLL(SingleNode<Object>*& head, Object givenValue, Object newValue) {//SingleNode refer to a single linked list
    SingleNode<Object>* newNode = new SingleNode<Object>(newValue);
    SingleNode<Object>* temp = head;
    for (; temp != nullptr; temp = temp->next ) {
        if (temp->data == givenValue) {
            newNode->next = temp->next;
            temp->next = newNode;
            return true;
        }
    }
    
    delete newNode;
    return false;
}
```

Funtion that find a given value and delete the node from the linked list. 
<br>Returns true if the deletion is successful, else false.</br>
```
template <typename Object>
bool eraseSLL(SingleNode<Object>*& head, Object givenValue) {
    if (head = nullptr) return false;
    for (SingleNode<Object>* temp = head; temp->next != nullptr; temp = temp->next ) {
        if (temp->next->data == givenValue) {
            SingleNode<Object>* p = temp->next;
            temp->next = temp->next->next;
            delete p;
            return true;
        } 
        else if ((temp->data == givenValue and temp == head)) {
            SingleNode<Object>* p = temp;
            head = temp->next;
            delete p;
            return true;
        }
    }
 
    return false;
}
```

Function that finds a given value and inserts a new node before it with a new value. 
<br>Returns true if the insertion is successful, else false.</br>
```
template <typename Object>
bool insertBeforeDLL(DoubleNode<Object>* & head, Object givenValue, Object newValue) {
    DoubleNode<Object>* newNode = new DoubleNode<Object>(newValue);
    DoubleNode<Object>* temp = head; 
    if (head == nullptr) return false;
    for(auto itr = head; itr->next != nullptr; itr = itr->next) {
        if(itr->data == givenValue and itr != head) {//get pointer of given value
            newNode->next = itr;
            newNode->prev = itr->prev;
            itr->prev->next = newNode;
            itr->prev = newNode;
            return true;
        }
        else if(head->data == givenValue) {
            newNode->next = temp;
            temp->prev = newNode;
            head = newNode;
            return true;
        }
    }
    
    delete newNode
    return false;
}
```

Function that finds a given value and deletes the matching node from the linked list. 
<br>Returns true if the insertion is successful, else false.</br>
```
template <typename Object>
bool eraseInDLL(DoubleNode<Object>*& head, Object givenValue) {
    if (head == nullptr) return false;
    for(auto itr = head; itr->next != nullptr; itr = itr->next) {
        if(itr->data == givenValue and itr != head) {
            itr->prev->next = itr->next;
            itr->next->prev = itr->prev;
            delete itr;
            return true;
        } 
        else if(head->data == givenValue) {
            head = head->next;
            delete itr;
            return true;
        }
    }
 
 return false;
}
```

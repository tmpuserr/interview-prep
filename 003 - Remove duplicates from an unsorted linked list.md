# Remove duplicates from an unsorted linked list

#### Implementation
```cpp
class Solution {
public:
    //Function to remove duplicates from unsorted linked list.
    Node * removeDuplicates( Node *head) {
        // your code goes here
        unordered_set<int> st;
        Node *dummyHead = new Node(0), *tail = dummyHead;
        while(head) {
            if(!st.count(head->data)) {
                tail->next = new Node(head->data);
                tail = tail->next;
                head = head->next;
                st.insert(tail->data);
            } else {
                Node *tmp = head;
                head = head->next;
                tmp->next = nullptr;
                delete tmp;
            }
        }
        return dummyHead->next;
    }
};
```

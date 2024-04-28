class Solution{
    public:
    Node* deleteMid(Node* head)
    {
        // Your Code Here
        if(head==NULL)
        {
            return head;
        }
        Node*temp=head;
        int count=0;
        while(temp!=nullptr)
        {
            count++;
            temp=temp->next;
        }
        // cout<<count;
        if(count==1)
        {
            return NULL;
        }
        int n=count/2;
        n=n-1;
        Node*curr=head;
        while(n!=0)
        {
            curr=curr->next;
            n--;
        }
        Node*temp1=curr->next;
        curr->next=curr->next->next;
        
        return head;
        
    }
};

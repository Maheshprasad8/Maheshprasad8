*******28th April 2024**************

**Binary Search Tree**


***236..Lowest Common Ancestor of a Binary Tree**
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL){
            return root;
        }
        if(root->val==p->val || root->val==q->val){
            return root;

        }
        TreeNode* leftAns=lowestCommonAncestor(root->left,p,q);
        TreeNode* rightAns=lowestCommonAncestor(root->right,p,q);
        if(leftAns!=NULL && rightAns!=NULL){
            return root;
        }
        else if(leftAns!=NULL && rightAns==NULL){
            return leftAns;
        }
        else if(leftAns==NULL && rightAns!=NULL){
        return rightAns;
        }
        else {
        return NULL;
        }
    }
};


*****235..Lowest Common Ancestor of a Binary Search Tree******
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        // if(root==NULL){
        //     return root;
        // }
        // if(root->val==p->val || root->val==q->val){
        //     return root;
        // }
        // TreeNode* leftAns=lowestCommonAncestor(root->left,p,q);
        // TreeNode* rightAns=lowestCommonAncestor(root->right,p,q);
        // if(leftAns!=NULL && rightAns!=NULL){
        //     return root;
        // }
        // else  if(leftAns!=NULL && rightAns==NULL){
        //     return leftAns;
        // }
        // else  if(leftAns==NULL && rightAns!=NULL){
        //     return rightAns;
        // }
        // else{
        //     return NULL;
        // }

        if(root==NULL){
            return root;
        }
        if(root->val < p->val && root->val<q->val){
            return lowestCommonAncestor(root->right,p,q);
        }
        if(root->val >p->val && root->val > q->val){
            return lowestCommonAncestor(root->left,p,q);
        }
        return root;
    }
};


****108**Convert Sorted Array to Binary Search Tree**********
class Solution {
    private:
     TreeNode* constructBST(vector<int>& nums, int left, int right) {
      if(left > right){
return NULL;
      }
      int mid=left+(right-left)/2;
      TreeNode* root=new TreeNode(nums[mid]);
      root->left=constructBST(nums,left,mid-1);
       root->right=constructBST(nums,mid+1,right);
        return root;
       }
  
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
      if(nums.empty()){
        return NULL;
      }  
      return constructBST(nums,0,nums.size()-1);
    }
      
};

********109..Convert Sorted List to Binary Search Tree***********
class Solution {
    private:
    TreeNode* constructBST(vector<int>&nums,int left ,int right){
        if(left >right){
            return NULL;
        }
        int mid=left+(right-left)/2;
        TreeNode* root=new TreeNode(nums[mid]);
        root->left=constructBST(nums,left,mid-1);
        root->right=constructBST(nums,mid+1,right);
        return root;
    }
public:
    TreeNode* sortedListToBST(ListNode* head) {
       vector<int>nums;
       ListNode* curr=head;
       while(curr!=NULL){
        nums.push_back(curr->val);
        curr=curr->next;
       } 
return constructBST(nums,0,nums.size()-1);
    }
};

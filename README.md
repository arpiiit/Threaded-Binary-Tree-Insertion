# Threaded-Binary-Tree-Insertion
import java.util.*;
class solution
{
static class Node
{
     Node left, right;
    int info;
    boolean lthread;
    boolean rthread;
};
   
static Node insert( Node root, int ikey)
{
  
    Node ptr = root;
    Node par = null; // Parent of key to be inserted
    while (ptr != null)
    {
      
        if (ikey == (ptr.info))
        {
            System.out.printf("Duplicate Key !\n");
            return root;
        }
   
        par = ptr; // Update parent pointer
   
        if (ikey < ptr.info)
        {
            if (ptr . lthread == false)
                ptr = ptr . left;
            else
                break;
        }
   
     
        else
        {
            if (ptr.rthread == false)
                ptr = ptr . right;
            else
                break;
        }
    }
   
   
    Node tmp = new Node();
    tmp . info = ikey;
    tmp . lthread = true;
    tmp . rthread = true;
     
    if (par == null)
    {
        root = tmp;
        tmp . left = null;
        tmp . right = null;
    }
    else if (ikey < (par . info))
    {
        tmp . left = par . left;
        tmp . right = par;
        par . lthread = false;
        par . left = tmp;
    }
    else
    {
        tmp . left = par;
        tmp . right = par . right;
        par . rthread = false;
        par . right = tmp;
    }
   
    return root;
}
   
static  Node inorderSuccessor( Node ptr)
{
   
    if (ptr . rthread == true)
        return ptr.right;
   
  
    ptr = ptr . right;
    while (ptr . lthread == false)
        ptr = ptr . left;
    return ptr;
}
   
static void inorder( Node root)
{
    if (root == null)
        System.out.printf("Tree is empty");
   
     Node ptr = root;
    while (ptr . lthread == false)
        ptr = ptr . left;
   
    while (ptr != null)
    {
        System.out.printf("%d ",ptr . info);
        ptr = inorderSuccessor(ptr);
    }
}
public static void main(String[] args)
{
     Node root = null;
   
    root = insert(root, 20);
    root = insert(root, 10);
    root = insert(root, 30);
    root = insert(root, 5);
    root = insert(root, 16);
    root = insert(root, 14);
    root = insert(root, 17);
    root = insert(root, 13);
   
    inorder(root);
} 
}

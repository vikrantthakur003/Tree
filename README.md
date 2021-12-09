import com.sun.source.tree.Tree;

public class tree_1 {

    static class HelloWorld {
        private static TreeNode root;

        private static class TreeNode{
            private TreeNode left;
            private TreeNode right;
            private int data;

            public TreeNode(int data){
                this.data = data;
            }
        }
        public void preorder(TreeNode root){
            if(root==null){
                return;
            }

            System.out.print(root.data+" ");
            preorder(root.left);
            preorder(root.right);

        }
        public void postorder(TreeNode root){
            if(root == null){
                return;
            }
            postorder(root.left);
            postorder(root.right);
            System.out.print(root.data+" ");
        }
        public void inorder(TreeNode root){
            if(root == null){
                return;
            }
            inorder(root.left);
            System.out.print(root.data+" ");
            inorder(root.right);
        }
        public TreeNode search(TreeNode root,int key){
            if(root==null){
                return root;
            }
            else if(key==root.data){
                return root;
            }
            else if(key<root.data){
                return search(root.left,key);
            }
            else{
                return search(root.right,key);
            }
        }
        public TreeNode searchIter(TreeNode root,int key){
            while(root!=null){
                if(key== root.data){
                    return root;
                }
                else if(key< root.data){
                    root = root.left;
                }
                else{
                    root = root.right;
                }
            }
            return null;
        }
        public static void insertion(TreeNode root,int key){
            TreeNode current = null;
            while(root!=null){
                current = root;
                if(key== root.data){
                    System.out.println("Cannot Insert this key already insert in Tree");
                }
                else if(key< root.data){
                    root = root.left;
                }
                else{
                    root = root.right;
                }
            }
            TreeNode newNode = new TreeNode(key);
            if (key<current.data){
                current.left = newNode;
            }
            else{
                current.right = newNode;
            }
        }
        public static TreeNode inorederpredecessor(TreeNode root){
            root = root.left;
            while(root.right!=null){
                root = root.right;
            }
            return root;
        }
        public static TreeNode deletion(TreeNode root,int key){
            TreeNode ipre;
            if(root==null){
                return null;
            }
            if(root.left==null && root.right==null){
               return null;
            }
            if(key< root.data){
                root.left = deletion(root.left,key);
            }
            if(key<root.data){
                root.right = deletion(root.right,key);
            }
            else{
                ipre = inorederpredecessor(root);
                root.data= ipre.data;
                root.left = deletion(root.left,ipre.data);
            }
            return root;
        }
        void createtree(){
            TreeNode first = new TreeNode(12);
            TreeNode r1 = new TreeNode(8);
            TreeNode r2 = new TreeNode(15);
            TreeNode r11 = new TreeNode(5);
            TreeNode r12 = new TreeNode(10);
            TreeNode r22 = new TreeNode(20);

            root = first;
            first.left = r1;
            first.right = r2;
            r1.left = r11;
            r1.right = r12;
            r2.right = r22;
        }


        public static void main(String[] args) {
            HelloWorld b1 = new HelloWorld();
            b1.createtree();
          /*  System.out.print("PREORDER----------> ");
            b1.preorder(b1.root);
            System.out.print("\nPOSTORDER----------> ");
            b1.postorder(b1.root);
            System.out.print("\nINORDER----------> ");
            b1.inorder(b1.root); */


//            System.out.println("\nSearching--------->");
//            if(null!=b1.search(root,200)){
//                System.out.println("Key Found !!!");
//            }
//            else{
//                System.out.println("Key Not Found !!!");
//            }

//            if(b1.searchIter(root,12)!=null){
//                System.out.println("Key Found !!!");
//            }
//            else{
//                System.out.println("Not Found !!!");
//            }
//            insertion(root,12);
//            System.out.print("PREORDER----------> ");
//            b1.preorder(b1.root);
//            System.out.print("\nINORDER----------> ");
//            b1.inorder(b1.root);

            System.out.print("\nINORDER----------> ");
            b1.inorder(b1.root);
            b1.deletion(root,15);
            System.out.print("\nINORDER----------> ");
            b1.inorder(b1.root);
        }
    }


    }



# lab5

public class MyLinkedList<E> {
    private Node<E> head;
    private Node<E> tail;
    private int size=0;

    public MyLinkedList() {
        this.head =null;
        this.tail =null;
    }
    
    public void addFirst(E e) {
Node<E> newNode = new Node<>(e);
newNode.next = head; 
head = newNode;
size++; 
if (tail == null)
tail = head;
    }
   
    public void addLast(E e) {
if (tail == null) {
head = tail = new Node<>(e);
}
else {
tail.next = new Node<>(e); 
tail = tail.next; 
}
size++;
}

 public void add(int i, E e){
     if(i==0)
         addFirst(e);
     else if(i>=size)
         addLast(e);
     else{
         Node<E>current=head;
         for(int num=1;num<i;num++)
             current=current.next;
         Node<E> temp=current.next;
         current.next=new Node<E>(e);
         (current.next).next=temp;
         size++;
     }
 }
 
 public E removeFirst() {
if (size == 0) 
    return null; 
else {
Node<E> temp = head; 
head = head.next; 
size--; 
if (head == null) 
    tail = null; 
return temp.element; 
}
}
 
 public E removeLast() {
if (size == 0) 
    return null;
else if (size == 1) {
Node<E> temp = head;
head = tail = null;
size = 0;
return temp.element;
}
else{
Node<E> current = head;
for (int i = 0; i < size - 2; i++)
current = current.next;
Node<E> temp = tail;
tail = current;
tail.next = null;
size--;
return temp.element;
}
}
 
 public E remove(int index) {
if (index < 0 || index >= size) 
    return null; 
else if (index == 0) 
    return removeFirst(); 
else if (index == size - 1) 
    return removeLast(); 
else {
Node<E> previous = head; 
for (int i = 1; i < index; i++) {
previous = previous.next; 
}
Node<E> current = previous.next; 
previous.next = current.next; 
size--; 
return current.element;
}
}
 
 public void add(E e){
     if(size==0)
         addFirst(e);
     else
         addLast(e);
 }
 
 public boolean contains(E e){
     boolean a= false;
     if(size==0)
         return a;
     Node<E> current=head;
         if (current.element==e)
         a=true;
     for(int i=0;i<size;i++){
         current=current.next;
          if (current.element==e)
         a=true;
     }
     return a;
 }
 public E get(int i){
     Node<E> current=head;
     if(i==0)
         return head.element;
     else if(i>=size-1)
         return tail.element;
     else{
         for(int o=0;o<i;o++){
            current=current.next; 
         }
      return current.element;}
 }
 
 public E getFirst(){
     return head.element;
 }
 
 public E getLast(){
    return tail.element;
}
 
 public int indexOf(E e){
     int i=-1; 
     boolean found=false;
     Node<E> current= head;
         for(int m=0;m<size-1;m++){
             if(current.element.equals(e)){
                 if(found=false)
                 i=m;
             found=true;
             }
            
             current=current.next;
             
         
     }   
     return i;
 }
 
 public int lastIndexOf(E e){
   int i=-1;
     Node<E> current= head;
     for(int m=0;m<size-1;m++){
          if(current.element.equals(e))
              i=m;
          current=current.next;
     }
    return i;
 }

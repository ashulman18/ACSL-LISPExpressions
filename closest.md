# ACSL-LISPExpressions

//Andrea Shulman
//LISP Expressions
//Contest #2

import javax.swing.JOptionPane;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Collections;

public class LISPExpressions
{
   private String expr;
   private String [] lines;
   private String [] commands;
   private int count;
   private String ret;
   private ArrayList<String> sub;
   private ArrayList<String> hold;
   private ArrayList<Integer> paren;
   
   public LISPExpressions()
   {
      lines= new String[5];
      commands=new String[5];
      count=0;
      ret="";
      sub=new ArrayList<String>();
      hold=new ArrayList<String>();
      paren=new ArrayList<Integer>(); 
      expr=JOptionPane.showInputDialog("Give a valid arithmetic LISP expression");
      String temp=expr;
      for (int index = temp.indexOf("(");index >= 0;index = temp.indexOf("(", index + 1))
         paren.add(index);
      for(int p=0;p<paren.size()-1;p++)
         sub.add(expr.substring(paren.get(p)+1,paren.get(p+1)));
      sub.add(expr.substring(paren.get(paren.size()-1)+1,expr.length()-1));
      for(int q=0;q<sub.size();q++)
         hold.add(sub.get(q));
      for(int j=0;j<5;j++)
         lines[j]=JOptionPane.showInputDialog("Command");
      for(int i=0;i<5;i++)
      {
         if(lines[i].indexOf(" ")!=-1)
            commands[i]=lines[i].substring(0,lines[i].indexOf(" "));
         else
            commands[i]=lines[i];
      }
      for(int k=0;k<5;k++)
      {
         count++;
         if(commands[k].equals("COUNT"))
            count(lines[k]);
         else if(commands[k].equals("REMOVE"))
            remove(lines[k]);
         else if(commands[k].equals("SORT"))
            sort(lines[k]);
         else if(commands[k].equals("REVERSE"))
            reverse(lines[k]);
         else if(commands[k].equals("MAXIMUM"))
            maximum(lines[k]);
         sub=hold;
      }
   }
   
   public void count(String str)
   {
      System.out.println(count+". "+(sub.size()-1));
   }
   
   public void remove(String str)
   {
      ret="";
      sub=hold;
      String tempor=str.substring(str.indexOf(" ")+1);
      int fir=Integer.parseInt(str.substring(str.indexOf(" ")+1,str.indexOf(" ")+1+tempor.indexOf(" ")));
      tempor=str.substring(str.indexOf(""+fir)+2);
      int sec=Integer.parseInt(tempor);
      for(int k=0;k<fir;k++)
         ret+="("+sub.get(k);
      for(int j=sec+1;j<sub.size();j++)
         ret+="("+sub.get(j);
      System.out.println(count+". "+ret);
   }
   
   public void sort(String str)
   {
      ret="";
      String tempor=str.substring(str.indexOf(" ")+1);
      int fir=Integer.parseInt(str.substring(str.indexOf(" ")+1,str.indexOf(" ")+1+tempor.indexOf(" ")));
      tempor=str.substring(str.indexOf(""+fir)+2);
      int sec=Integer.parseInt(tempor);
      String[]temp= new String[sec-fir+1];
      int counter=0;
      for(int i=fir;i<sec+1;i++)
      {
         temp[counter]=sub.get(i);
         counter++;
      }
      Arrays.sort(temp);
      counter=0;
      for(int j=fir;j<sec+1;j++)
      {
         sub.set(j,temp[counter]);
         counter++;
      }
      for(int k=0;k<sub.size();k++)
         ret+="("+sub.get(k);
      System.out.println(count+". "+ret+")");
      //sub=hold;
   }
   
   public void reverse(String str)
   {
      ret="";
      String tempor=str.substring(str.indexOf(" ")+1);
      int fir=Integer.parseInt(str.substring(str.indexOf(" ")+1,str.indexOf(" ")+1+tempor.indexOf(" ")));
      tempor=str.substring(str.indexOf(""+fir)+2);
      int sec=Integer.parseInt(tempor);
      List<String> temp=sub.subList(fir,sec+1);
      Collections.reverse(temp);
      int val=0;
      for(int k=0;k<fir;k++)
         ret+="("+sub.get(k);
      for(int i=0;i<temp.size();i++)
         ret+="("+temp.get(i);
      for(int j=sec+1;j<sub.size();j++)
         ret+="("+sub.get(j);
      System.out.println(count+". "+ret+")");
   }

   public void maximum(String str)
   {
      String most="";
      int amt=0;
      for(int i=0;i<sub.size();i++)
      {
         if(sub.get(i).length()>amt)
         {
            most=sub.get(i);
            amt=sub.get(i).length();
         }
      }
      System.out.println(count+". ("+most);
   }
   
   public static void main (String[]args)
   {
      LISPExpressions test = new LISPExpressions();
   }
}

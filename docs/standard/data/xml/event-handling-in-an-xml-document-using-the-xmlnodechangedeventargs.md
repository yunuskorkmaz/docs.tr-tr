---
title: Olay bir XML belgesinde XmlNodeChangedEventArgs kullanarak işleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c382b22825512000a906af8a865b6b7c5f4c73c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204896"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a>Olay bir XML belgesinde XmlNodeChangedEventArgs kullanarak işleme
**XmlNodeChangedEventArgs** kayıtlı olay işleyicileri için geçirilen bağımsız değişkenler kapsülleyen **XmlDocument** olayları işlemek için nesne. Olayları ve ne zaman tetiklenir açıklaması aşağıdaki tabloda verilmiştir.  
  
|Olay|Tetiklendi|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|Geçerli belgeye ait bir düğüm hakkında başka bir düğüme eklenecek olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeInserted>|Zaman içinde başka bir düğüme geçerli belgeye ait bir düğüm eklenmiş.|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|Bu belgeye ait bir düğüm belgeden kaldırılmak üzere olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|Ne zaman bu belgeye ait bir düğümü üst öğesinden kaldırıldı.|  
|<xref:System.Xml.XmlDocument.NodeChanging>|Bir düğümün değerini değiştirilmek üzere olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeChanged>|Ne zaman bir düğümün değerini değiştirildi.|  
  
> [!NOTE]
>  Varsa **XmlDataDocument** bellek kullanımı kullanmak için iyileştirilmiş tam olarak **veri kümesi** depolama **XmlDataDocument** herhangi bir değişiklik olduğunda, yukarıda listelenen olaylar tetikleyebilir değil temel alınan yapılan **veri kümesi**. Bu olaylar gerekiyorsa, bütün geçiş **XmlDocument** tam olmayan en iyi duruma getirilmiş bellek kullanımı yapmak için bir kez.  
  
 Aşağıdaki kod örneği, bir olay işleyicisi tanımlama ve bir olay için olay işleyicisi ekleme gösterir.  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 Bazı XML belge nesne modeli (DOM) işlemler içinde birden çok olayı harekete sonuçlanabilen bileşik işlemlerdir. Örneğin, **AppendChild** önceki üst öğesinden eklenen düğümünü kaldırmak de olabilir. Bu durumda, gördüğünüz bir **NodeRemoved** önce tetiklenen olayı arkasından bir **NodeInserted** olay. İşlem ayarı ister **sınıfının InnerXml** içinde birden çok olayı neden olabilir.  
  
 Aşağıdaki kod örneği, olay işleyicisi oluşturmayı ve işlenmesi gösterir **NodeInserted** olay.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeChangedEventArgs> ve <xref:System.Xml.XmlNodeChangedEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

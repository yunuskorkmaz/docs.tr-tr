---
title: Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: 7bca8600468d3715b1d1cca46049eb07bb8e3d03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287785"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a>Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme
**XmlNodeChangedEventArgs** , olayları Işlemek için **XmlDocument** nesnesinde kayıtlı olan olay işleyicilerine geçirilen bağımsız değişkenleri kapsüller. Olaylar ve tetiklendiklerinde bir açıklama aşağıdaki tabloda verilmiştir.  
  
|Olay|Belirtildiği|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|Geçerli belgeye ait bir düğüm başka bir düğüme Eklenme konusunda olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeInserted>|Geçerli belgeye ait bir düğüm başka bir düğüme eklendiyse.|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|Bu belgeye ait bir düğüm belgeden kaldırılmak üzere olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|Bu belgeye ait bir düğüm, üst öğesinden kaldırıldığında.|  
|<xref:System.Xml.XmlDocument.NodeChanging>|Bir düğümün değeri değiştirilme için olduğunda.|  
|<xref:System.Xml.XmlDocument.NodeChanged>|Bir düğümün değeri değiştirildiğinde.|  
  
> [!NOTE]
> **XmlDataDocument** bellek kullanımı, **veri kümesi** depolamayı kullanmak için tamamen iyileştirilirse, temel alınan **veri kümesinde**değişiklik yapıldığında **XmlDataDocument** , yukarıda listelenen olayları tetiklemeyebilir. Bu olaylara ihtiyacınız varsa, bellek kullanımını tam olarak iyileştirilmemiş hale getirmek için **XmlDocument** 'ın tamamına bir kez geçiş yapmanız gerekir.  
  
 Aşağıdaki kod örneği bir olay işleyicisinin nasıl tanımlanacağını ve olay işleyicisinin bir olaya nasıl ekleneceğini gösterir.  
  
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
  
 Bazı XML Belge Nesne Modeli (DOM) işlemleri, birden çok olayın tetikedilmesine neden olan bileşik işlemlerdir. Örneğin, **AppendChild** 'ın önceki üst öğesinden eklenen düğümü kaldırmak da gerekebilir. Bu durumda, önce tetiklenen bir **Noderetaşınmış** olay, ardından **nodeınsertedbir** olay görürsünüz. **InnerXml** ayarı gibi işlemler birden çok olay oluşmasına neden olabilir.  
  
 Aşağıdaki kod örneğinde, olay işleyicisinin oluşturulması ve **Nodeınsertedetkinliğin** işlenmesi gösterilmektedir.  
  
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
  
 Daha fazla bilgi için <xref:System.Xml.XmlNodeChangedEventArgs> ve <xref:System.Xml.XmlNodeChangedEventHandler> bölümlerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

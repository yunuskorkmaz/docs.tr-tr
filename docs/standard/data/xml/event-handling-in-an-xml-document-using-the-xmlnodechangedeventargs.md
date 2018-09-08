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
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="2e13f-102">Olay bir XML belgesinde XmlNodeChangedEventArgs kullanarak işleme</span><span class="sxs-lookup"><span data-stu-id="2e13f-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="2e13f-103">**XmlNodeChangedEventArgs** kayıtlı olay işleyicileri için geçirilen bağımsız değişkenler kapsülleyen **XmlDocument** olayları işlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="2e13f-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="2e13f-104">Olayları ve ne zaman tetiklenir açıklaması aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e13f-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="2e13f-105">Olay</span><span class="sxs-lookup"><span data-stu-id="2e13f-105">Event</span></span>|<span data-ttu-id="2e13f-106">Tetiklendi</span><span class="sxs-lookup"><span data-stu-id="2e13f-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="2e13f-107">Geçerli belgeye ait bir düğüm hakkında başka bir düğüme eklenecek olduğunda.</span><span class="sxs-lookup"><span data-stu-id="2e13f-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="2e13f-108">Zaman içinde başka bir düğüme geçerli belgeye ait bir düğüm eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="2e13f-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="2e13f-109">Bu belgeye ait bir düğüm belgeden kaldırılmak üzere olduğunda.</span><span class="sxs-lookup"><span data-stu-id="2e13f-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="2e13f-110">Ne zaman bu belgeye ait bir düğümü üst öğesinden kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2e13f-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="2e13f-111">Bir düğümün değerini değiştirilmek üzere olduğunda.</span><span class="sxs-lookup"><span data-stu-id="2e13f-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="2e13f-112">Ne zaman bir düğümün değerini değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="2e13f-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2e13f-113">Varsa **XmlDataDocument** bellek kullanımı kullanmak için iyileştirilmiş tam olarak **veri kümesi** depolama **XmlDataDocument** herhangi bir değişiklik olduğunda, yukarıda listelenen olaylar tetikleyebilir değil temel alınan yapılan **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="2e13f-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="2e13f-114">Bu olaylar gerekiyorsa, bütün geçiş **XmlDocument** tam olmayan en iyi duruma getirilmiş bellek kullanımı yapmak için bir kez.</span><span class="sxs-lookup"><span data-stu-id="2e13f-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="2e13f-115">Aşağıdaki kod örneği, bir olay işleyicisi tanımlama ve bir olay için olay işleyicisi ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e13f-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
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
  
 <span data-ttu-id="2e13f-116">Bazı XML belge nesne modeli (DOM) işlemler içinde birden çok olayı harekete sonuçlanabilen bileşik işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="2e13f-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="2e13f-117">Örneğin, **AppendChild** önceki üst öğesinden eklenen düğümünü kaldırmak de olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e13f-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="2e13f-118">Bu durumda, gördüğünüz bir **NodeRemoved** önce tetiklenen olayı arkasından bir **NodeInserted** olay.</span><span class="sxs-lookup"><span data-stu-id="2e13f-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="2e13f-119">İşlem ayarı ister **sınıfının InnerXml** içinde birden çok olayı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e13f-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="2e13f-120">Aşağıdaki kod örneği, olay işleyicisi oluşturmayı ve işlenmesi gösterir **NodeInserted** olay.</span><span class="sxs-lookup"><span data-stu-id="2e13f-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
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
  
 <span data-ttu-id="2e13f-121">Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeChangedEventArgs> ve <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="2e13f-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e13f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e13f-122">See also</span></span>

- [<span data-ttu-id="2e13f-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2e13f-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

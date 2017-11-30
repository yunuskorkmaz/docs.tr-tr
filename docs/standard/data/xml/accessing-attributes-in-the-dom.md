---
title: "DOM özniteliklere erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="25870-102">DOM özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="25870-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="25870-103">Öğenin özelliklerini öğesinin alt öğeleri öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="25870-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="25870-104">Bu ayrım eşdüzey, üst ve alt düğümleri XML belge nesne modeli (DOM) gitmek için kullanılan yöntemleri nedeniyle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="25870-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="25870-105">Örneğin, **PreviousSibling** ve **NextSibling** yöntemleri bir öğeyi bir öznitelik veya öznitelikler arasında gezinmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="25870-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="25870-106">Bunun yerine, bir öznitelik, bir öğenin bir özelliktir ve sahibi bir öğe, sahip bir **OwnerElement** özelliği ve bir **parentNode** özelliği ve gezinti farklı yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="25870-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="25870-107">Geçerli düğüm öğenin olduğunda kullanın **HasAttribute** öğeyle ilişkili öznitelikleri olup olmadığını görmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="25870-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="25870-108">Bilinen bir öğe öznitelikleri sonra özniteliklere erişme birden çok yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="25870-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="25870-109">Tek bir öznitelik öğeyi almak için kullanabileceğiniz **GetAttribute** ve **GetAttributeNode** yöntemlerinin **XmlElement** veya tüm öznitelikleri elde edebilirsiniz bir koleksiyona.</span><span class="sxs-lookup"><span data-stu-id="25870-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="25870-110">Koleksiyon alma koleksiyon üzerinde yinelenecek gerektiğinde kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="25870-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="25870-111">Tüm öznitelikleri öğe istiyorsanız kullanın **öznitelikleri** bir koleksiyona tüm öznitelikleri almak için öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="25870-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="25870-112">Bir koleksiyona tüm öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="25870-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="25870-113">Tüm bir öğe düğümü özniteliklerini bir koleksiyona koymak istiyorsanız çağrısı **XmlElement.Attributes** özelliği.</span><span class="sxs-lookup"><span data-stu-id="25870-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="25870-114">Bu alır **XmlAttributeCollection** , bir öğenin tüm özniteliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="25870-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="25870-115">**XmlAttributeCollection** sınıfının devraldığı **XmlNamedNode** eşleme.</span><span class="sxs-lookup"><span data-stu-id="25870-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="25870-116">Bu nedenle, koleksiyonda kullanılabilen özellikleri ve yöntemleri adlandırılmış düğüm haritada kullanılabilir ayrıca yöntemlere ve özelliklere özgü dahil **XmlAttributeCollection** gibi sınıfı **ItemOf**  özelliği veya **Append** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="25870-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="25870-117">Öznitelik koleksiyondaki her öğe temsil eden bir **XmlAttribute** düğümü.</span><span class="sxs-lookup"><span data-stu-id="25870-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="25870-118">Öznitelik sayısı üzerinde bir öğeye bulmak için get **XmlAttributeCollection**ve **sayısı** görmek için özellik kaç **XmlAttribute** düğümleri koleksiyonunda olan.</span><span class="sxs-lookup"><span data-stu-id="25870-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="25870-119">Aşağıdaki kod örneği, bir öznitelik almak gösterilmiştir toplama ve kullanma **sayısı** yöntemi döngü dizini için yineleme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="25870-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="25870-120">Aşağıdaki kod sonra koleksiyondan tek öznitelik almak ve değerini görüntülemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="25870-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="25870-121">Bu örnekte aşağıdaki çıkış görüntüler:</span><span class="sxs-lookup"><span data-stu-id="25870-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="25870-122">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="25870-122">**Output**</span></span>  
  
 <span data-ttu-id="25870-123">Tüm öznitelikleri koleksiyonda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="25870-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="25870-124">Bir öznitelik koleksiyonu bilgilerinde adı veya dizin numarasını tarafından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="25870-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="25870-125">Yukarıdaki örnekte, ada göre verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25870-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="25870-126">Sonraki örnek dizin numarası ile verileri almak üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="25870-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="25870-127">Çünkü **XmlAttributeCollection** koleksiyonudur ve yinelendiğinde Bu örnek, adı veya dizin tarafından devralınırsa gösterir sıfır tabanlı dizini kullanarak ve aşağıdaki dosya kullanarak koleksiyonu dışında ilk öznitelik seçme **baseuri.xml**, giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="25870-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="25870-128">Giriş</span><span class="sxs-lookup"><span data-stu-id="25870-128">Input</span></span>  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="25870-129">Tek tek öznitelik düğümü alınıyor</span><span class="sxs-lookup"><span data-stu-id="25870-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="25870-130">Bir öğeden tek öznitelik düğümü almak için <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25870-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="25870-131">Türünde bir nesne döndürür **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="25870-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="25870-132">Bulduktan sonra bir **XmlAttribute**, tüm yöntemleri ve özellikleri bulunan <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> bulma gibi nesnesi üzerinde sınıf kullanılabilir **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="25870-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="25870-133">Önceki örnekte gösterildiği gibi tek öznitelik düğümü özniteliği koleksiyondan burada alınır da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25870-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="25870-134">Aşağıdaki kod örneğinde gösterildiği bir kod satırı tek öznitelik almak için dizin numarası ile XML belgesi kökünden yazılabilir nasıl ağaç, olarak da bilinen **DocumentElement** özelliği.</span><span class="sxs-lookup"><span data-stu-id="25870-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="25870-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25870-135">See Also</span></span>  
 [<span data-ttu-id="25870-136">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="25870-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

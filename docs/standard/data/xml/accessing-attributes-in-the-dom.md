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
# <a name="accessing-attributes-in-the-dom"></a>DOM özniteliklere erişme
Öğenin özelliklerini öğesinin alt öğeleri öznitelikleridir. Bu ayrım eşdüzey, üst ve alt düğümleri XML belge nesne modeli (DOM) gitmek için kullanılan yöntemleri nedeniyle önemlidir. Örneğin, **PreviousSibling** ve **NextSibling** yöntemleri bir öğeyi bir öznitelik veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, bir öznitelik, bir öğenin bir özelliktir ve sahibi bir öğe, sahip bir **OwnerElement** özelliği ve bir **parentNode** özelliği ve gezinti farklı yöntemleri vardır.  
  
 Geçerli düğüm öğenin olduğunda kullanın **HasAttribute** öğeyle ilişkili öznitelikleri olup olmadığını görmek için yöntem. Bilinen bir öğe öznitelikleri sonra özniteliklere erişme birden çok yöntemi vardır. Tek bir öznitelik öğeyi almak için kullanabileceğiniz **GetAttribute** ve **GetAttributeNode** yöntemlerinin **XmlElement** veya tüm öznitelikleri elde edebilirsiniz bir koleksiyona. Koleksiyon alma koleksiyon üzerinde yinelenecek gerektiğinde kullanışlı olur. Tüm öznitelikleri öğe istiyorsanız kullanın **öznitelikleri** bir koleksiyona tüm öznitelikleri almak için öğesi özelliği.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Bir koleksiyona tüm öznitelikleri alma  
 Tüm bir öğe düğümü özniteliklerini bir koleksiyona koymak istiyorsanız çağrısı **XmlElement.Attributes** özelliği. Bu alır **XmlAttributeCollection** , bir öğenin tüm özniteliklerini içerir. **XmlAttributeCollection** sınıfının devraldığı **XmlNamedNode** eşleme. Bu nedenle, koleksiyonda kullanılabilen özellikleri ve yöntemleri adlandırılmış düğüm haritada kullanılabilir ayrıca yöntemlere ve özelliklere özgü dahil **XmlAttributeCollection** gibi sınıfı **ItemOf**  özelliği veya **Append** yöntemi. Öznitelik koleksiyondaki her öğe temsil eden bir **XmlAttribute** düğümü. Öznitelik sayısı üzerinde bir öğeye bulmak için get **XmlAttributeCollection**ve **sayısı** görmek için özellik kaç **XmlAttribute** düğümleri koleksiyonunda olan.  
  
 Aşağıdaki kod örneği, bir öznitelik almak gösterilmiştir toplama ve kullanma **sayısı** yöntemi döngü dizini için yineleme üzerinde. Aşağıdaki kod sonra koleksiyondan tek öznitelik almak ve değerini görüntülemek nasıl gösterir.  
  
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
  
 Bu örnekte aşağıdaki çıkış görüntüler:  
  
 **Çıktı**  
  
 Tüm öznitelikleri koleksiyonda görüntüler.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 Bir öznitelik koleksiyonu bilgilerinde adı veya dizin numarasını tarafından alınabilir. Yukarıdaki örnekte, ada göre verileri gösterilmektedir. Sonraki örnek dizin numarası ile verileri almak üzere nasıl gösterir.  
  
 Çünkü **XmlAttributeCollection** koleksiyonudur ve yinelendiğinde Bu örnek, adı veya dizin tarafından devralınırsa gösterir sıfır tabanlı dizini kullanarak ve aşağıdaki dosya kullanarak koleksiyonu dışında ilk öznitelik seçme **baseuri.xml**, giriş olarak.  
  
### <a name="input"></a>Giriş  
  
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
  
## <a name="retrieving-an-individual-attribute-node"></a>Tek tek öznitelik düğümü alınıyor  
 Bir öğeden tek öznitelik düğümü almak için <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> yöntemi kullanılır. Türünde bir nesne döndürür **XmlAttribute**. Bulduktan sonra bir **XmlAttribute**, tüm yöntemleri ve özellikleri bulunan <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> bulma gibi nesnesi üzerinde sınıf kullanılabilir **OwnerElement**.  
  
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
  
 Önceki örnekte gösterildiği gibi tek öznitelik düğümü özniteliği koleksiyondan burada alınır da yapabilirsiniz. Aşağıdaki kod örneğinde gösterildiği bir kod satırı tek öznitelik almak için dizin numarası ile XML belgesi kökünden yazılabilir nasıl ağaç, olarak da bilinen **DocumentElement** özelliği.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

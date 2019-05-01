---
title: DOM Özniteliklerine Erişim
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08919e05f8396d37cb50ca24989b86000c854411
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921647"
---
# <a name="accessing-attributes-in-the-dom"></a>DOM Özniteliklerine Erişim

Öznitelikleri öğesi, öğenin alt öğelerine özellikleridir. Bu ayrım eşdüzey, üst ve alt düğümleri XML belge nesne modeli (DOM) gezinmek için kullanılan yöntemleri nedeniyle büyük/küçük harf önemlidir. Örneğin, **PreviousSibling** ve **NextSibling** yöntemleri öğeden bir özniteliği veya öznitelikleri arasında gezinmek için kullanılmaz. Bunun yerine bir öznitelik bir öğenin bir özelliktir ve sahibi bir öğe, sahip bir **OwnerElement** özelliği değil bir **özelliğindeki** özelliği ve gezinti farklı yöntemleri vardır.

Geçerli düğüm bir öğe olduğunda kullanın **HasAttribute** öğeyle ilişkili herhangi bir özniteliği olup olmadığını görmek için yöntemi. Bir öğenin öznitelikleri tanındıktan sonra özniteliklere erişim için birden fazla yöntem vardır. Tek bir öznitelik öğeden geri almak için kullanabileceğiniz **GetAttribute** ve **GetAttributeNode** yöntemlerinin **XmlElement** veya tüm öznitelikleri edinebilirsiniz bir koleksiyona. Koleksiyon alma koleksiyon üzerinde yinelemek istiyorsanız kullanışlıdır. Öğenin tüm öznitelikleri istiyorsanız kullanın **öznitelikleri** öğe bir koleksiyona tüm öznitelikleri almak için özellik.

## <a name="retrieving-all-attributes-into-a-collection"></a>Bir koleksiyona tüm özniteliklerini alma

Tüm öznitelikleri bir öğe düğümünün bir koleksiyona koymak istiyorsanız, çağrı **XmlElement.Attributes** özelliği. Bu alır **XmlAttributeCollection** , bir öğenin tüm özniteliklerini içerir. **XmlAttributeCollection** sınıfının devraldığı **XmlNamedNode** eşleme. Bu nedenle, yöntemleri ve özellikleri koleksiyonunda kullanılabilir bir adlandırılmış düğümün haritada mevcut kodlar ayrıca yöntemlere ve özelliklere özgü dahil **XmlAttributeCollection** gibi sınıf **ItemOf**  özelliği veya **ekleme** yöntemi. Öznitelik koleksiyondaki her öğe temsil eden bir **XmlAttribute** düğümü. Bir öğe üzerinde öznitelik sayısını bulmak için alma **XmlAttributeCollection**ve **sayısı** görmek için özellik kaç **XmlAttribute** düğümlerdir koleksiyonu.

Aşağıdaki kod örneği, bir özniteliği almayı gösterilmektedir toplama ve kullanma **sayısı** üzerinde yineleme döngü dizini için yöntemi. Kodu daha sonra tek bir öznitelik koleksiyonundan alma ve değerinin görüntülendiğini gösterir.

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

Bu örnek aşağıdaki çıkışı görüntüler:

**Output**

Koleksiyondaki tüm öznitelikleri görüntüler.

```
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

Bir öznitelik koleksiyonu bilgileri adı veya dizin numarası tarafından alınabilir. Yukarıdaki örnekte, ada göre veri almak gösterilmektedir. Sonraki örnek dizin numarası ile verileri almak üzere nasıl gösterir.

Çünkü **XmlAttributeCollection** koleksiyonudur ve yinelendiğinde adı veya dizin tarafından devralınırsa, bu örnek gösterir ilk özniteliği sıfır tabanlı dizin ve şu dosyayı kullanarak koleksiyon dışında seçerek **baseuri.xml**, giriş olarak.

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
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
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
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a>Tek bir öznitelik düğümü alınıyor

Bir öğe, tek öznitelik düğümü alınacağını <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> yöntemi kullanılır. Türünde bir nesne döndürür **XmlAttribute**. Sonra bir **XmlAttribute**, tüm yöntemler ve özellikler kullanılabilir <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> bulma gibi o nesne üzerindeki sınıf kullanılabilir **OwnerElement**.

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

Önceki örnekte gösterilen şekilde tek öznitelik düğümü öznitelik koleksiyonundan alınır burada da yapabilirsiniz. Aşağıdaki kod örneğinde gösterildiği bir kod satırı tek bir özniteliği almayı dizin numarası ile XML belgesi kökünden yazılabilir nasıl ağacı, olarak da bilinen **DocumentElement** özelliği.

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

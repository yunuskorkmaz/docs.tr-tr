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
ms.openlocfilehash: 272c224c8a1c5061392856685f374237f8a10579
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956868"
---
# <a name="accessing-attributes-in-the-dom"></a>DOM Özniteliklerine Erişim

Öznitelikleri, öğesinin alt öğesi değil, öğesinin özelliklerdir. Bu ayrım, XML Belge Nesne Modeli (DOM) eşdüzey, üst ve alt düğümlerine gitmek için kullanılan yöntemler nedeniyle önemlidir. Örneğin, **previouseşdüzey** ve **nexteşdüzey** Yöntemler bir öğeden bir özniteliğe veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, bir özniteliği bir öğesinin özelliğidir ve bir öğesi tarafından sahiplenilir ve **ParentNode** özelliğine **sahip** değildir ve farklı gezinme yöntemlerine sahiptir.

Geçerli düğüm bir öğe olduğunda, öğesiyle ilişkili herhangi bir öznitelik olup olmadığını görmek için **HasAttribute** metodunu kullanın. Bir öğenin öznitelikleri olduğu bilindiğinde, özniteliklere erişmek için birden çok yöntem vardır. Öğesinden tek bir özniteliği almak için, **XmlElement** 'Nin **GetAttribute** ve **GetAttributeNode** yöntemlerini kullanabilirsiniz veya tüm öznitelikleri bir koleksiyonda elde edebilirsiniz. Koleksiyonu yinelemek gerekirse, koleksiyonu almak yararlı olur. Öğesinin tüm özniteliklerini istiyorsanız, tüm özniteliklerini bir koleksiyona almak için öğesinin **Attributes** özelliğini kullanın.

## <a name="retrieving-all-attributes-into-a-collection"></a>Tüm öznitelikleri bir koleksiyona alma

Bir öğe düğümünün tüm özniteliklerinin bir koleksiyona yerleştirileceğini istiyorsanız, **XmlElement. Attributes** özelliğini çağırın. Bu, bir öğenin tüm özniteliklerini içeren **XmlAttributeCollection** 'ı alır. **XmlAttributeCollection** sınıfı **xmlnamednode** eşlemesinden devralır. Bu nedenle, koleksiyonda bulunan Yöntemler ve özellikler, **XmlAttributeCollection** sınıfına özgü yöntemlere ve özelliklere ek olarak adlandırılmış bir düğüm eşlemesinde bulunan özellikleri içerir, örneğin **ItemOf** özelliği veya **append** yöntemi. Öznitelik koleksiyonundaki her öğe bir **XmlAttribute** düğümünü temsil eder. Bir öğedeki öznitelik sayısını bulmak için **XmlAttributeCollection**' ı alın ve koleksiyonda kaç **XmlAttribute** düğümünün olduğunu görmek için **Count** özelliğini kullanın.

Aşağıdaki kod örneği, bir öznitelik koleksiyonunun nasıl alınacağını ve döngü dizini için **Count** yönteminin nasıl kullanılacağını gösterir. Kod bundan sonra koleksiyondan tek bir özniteliğin nasıl alınacağını ve değerinin nasıl görüntüleneceğini gösterir.

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

Bu örnek aşağıdaki çıktıyı görüntüler:

**Output**

Koleksiyondaki tüm öznitelikleri görüntüleyin.

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

Bir öznitelik koleksiyonundaki bilgiler, ad veya dizin numarası ile alınabilir. Yukarıdaki örnekte, verilerin ada göre nasıl alınacağını gösterilmektedir. Sonraki örnek, verilerin dizin numarasına göre nasıl alınacağını gösterir.

**XmlAttributeCollection** bir koleksiyon olduğundan ve ad ya da dizine göre yinelenebilir olduğundan, bu örnek, sıfır tabanlı bir dizin kullanarak koleksiyonun ilk özniteliğini seçip giriş olarak **baseUri. xml**dosyasını kullanarak gösterir.

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

## <a name="retrieving-an-individual-attribute-node"></a>Tek bir öznitelik düğümünü alma

Bir öğeden tek bir öznitelik düğümü almak için <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> yöntemi kullanılır. **XmlAttribute**türünde bir nesne döndürür. Bir **XmlAttribute**olduktan sonra, <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> sınıfında bulunan tüm yöntemler ve özellikler, **Owner öğesini**bulma gibi bu nesnede kullanılabilir.

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

Ayrıca, bir önceki örnekte gösterildiği gibi, öznitelik koleksiyonundan tek bir öznitelik düğümü alındığında da yapabilirsiniz. Aşağıdaki kod örneği, **DocumentElement** özelliği olarak da bilinen XML belge ağacının kökünden dizin numarasıyla tek bir özniteliği almak için nasıl bir kod satırı yazılacağını gösterir.

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

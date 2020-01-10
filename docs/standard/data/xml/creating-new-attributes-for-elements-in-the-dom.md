---
title: DOM Öğeleri için Yeni Öznitelikler Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711018"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>DOM Öğeleri için Yeni Öznitelikler Oluşturma

Yeni özniteliklerin oluşturulması diğer düğüm türlerini oluşturmaktan farklıdır, çünkü öznitelikler düğüm değildir, ancak bir öğe düğümünün özellikleri olduğundan ve öğesiyle ilişkili bir **XmlAttributeCollection** içinde yer alır. Bir öznitelik oluşturup bir öğeye iliştirmek için birden çok yol vardır:

- Öğe düğümünü alın ve bu öğenin öznitelik koleksiyonuna bir öznitelik eklemek için **SetAttribute** kullanın.

- **CreateAttribute** metodunu kullanarak bir **XmlAttribute** düğümü oluşturun, öğe düğümünü alın, sonra düğümü bu öğenin öznitelik koleksiyonuna eklemek için **SetAttributeNode** kullanın.

Aşağıdaki örnek **SetAttribute** yöntemi kullanılarak bir öğeye bir özniteliği nasıl ekleneceğini göstermektedir:

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
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
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

Aşağıdaki örnek, **CreateAttribute** yöntemi kullanılarak oluşturulan yeni bir özniteliği gösterir. Daha sonra, **SetAttributeNode** yöntemini kullanarak **Book** öğesinin öznitelik koleksiyonuna eklenen özniteliği gösterir.

Aşağıdaki XML verildiğinde:
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

Yeni bir öznitelik oluşturun ve bu değere bir değer verin:

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

ve öğesini öğesine ekleyin:

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

**Output**

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

Tam kod örneği <xref:System.Xml.XmlDocument.CreateAttribute%2A>' de bulunabilir.

Ayrıca, bir **XmlAttribute** düğümü oluşturabilir ve bunu koleksiyondaki uygun konuma yerleştirmek Için **InsertBefore** veya **InsertAfter** yöntemlerini kullanabilirsiniz. Öznitelik koleksiyonunda aynı ada sahip bir öznitelik zaten varsa, var olan **XmlAttribute** düğümü koleksiyondan kaldırılır ve yeni **XmlAttribute** düğümü eklenir. Bu, **SetAttribute** yöntemiyle aynı şekilde çalışır. Bu yöntemler, var olan bir düğümü bir parametre olarak, **InsertBefore** ve **InsertAfter**yapmak için başvuru noktası olarak alır. Yeni düğümün nereye yerleştirileceğini belirten bir başvuru düğümü sağlamazsanız, **InsertAfter** yöntemi için varsayılan değer, koleksiyonun başlangıcına yeni düğüm eklemek olur. Hiçbir başvuru düğümü sağlanmazsa, **InsertBefore**varsayılan konumu koleksiyonun sonunda olur.

Özniteliklerin **XmlNamedNodeMap** oluşturduysanız, <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> yöntemini kullanarak bir özniteliği ada göre ekleyebilirsiniz. Daha fazla bilgi için bkz. [NamedNodeMaps ve NodeLists Içindeki düğüm koleksiyonları](node-collections-in-namednodemaps-and-nodelists.md).

## <a name="default-attributes"></a>Varsayılan öznitelikler

Varsayılan bir özniteliğe sahip olarak belirtilen bir öğesi oluşturursanız, varsayılan değeri olan yeni bir varsayılan öznitelik, XML Belge Nesne Modeli (DOM) tarafından oluşturulur ve öğesine eklenir. Varsayılan özniteliğin alt düğümleri de şu anda oluşturulur.

## <a name="attribute-child-nodes"></a>Öznitelik alt düğümleri

Öznitelik düğümünün değeri, alt düğümleri haline gelir. Yalnızca iki tür geçerli alt düğüm vardır: **XmlText** düğümleri ve **XmlEntityReference** düğümleri. Bunlar, **FirstChild** ve **LastChild** gibi yöntemlerin alt düğümler olarak işlenmesi açısından önemli olan alt düğümlerdir. Alt düğümlere sahip bir özniteliğin bu ayrım özelliği, öznitelikleri veya öznitelik alt düğümlerini kaldırmaya çalışırken önemlidir. Daha fazla bilgi için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](removing-attributes-from-an-element-node-in-the-dom.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

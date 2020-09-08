---
title: XML bildirimiyle serileştirme-LINQ to XML
description: C# veya Visual Basic XML seri hale getirmek istediğinizde bir XML bildiriminin oluşturulup oluşturulmayacağını kontrol edebilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 8d25d199b149ac6aeb2aa37dc248523e79847220
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552956"
---
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a>XML bildirimiyle serileştirme (LINQ to XML)

Bu makalede, C# veya Visual Basic XML seri hale geldiğinde bir XML bildiriminin oluşturulup oluşturulmayacağını nasıl denetleyen açıklanır.

<xref:System.IO.File>Yöntemini veya yöntemini kullanarak bir veya öğesine serileştirmek BIR <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> XML bildirimi oluşturur. ' A serileştirçalıştığınızda <xref:System.Xml.XmlWriter> , yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilir) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.

Yöntemini kullanarak bir dizeye seri hale getiriyorsanız `ToString` , sonuçta elde EDILEN XML BIR XML bildirimi içermez.

## <a name="example-serialize-with-an-xml-declaration"></a>Örnek: bir XML bildirimiyle serileştirme

Aşağıdaki örnek bir dosyası oluşturur <xref:System.Xml.Linq.XElement> , belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:

```csharp
XElement root = new XElement("Root",
    new XElement("Child", "child content")
);
root.Save("Root.xml");
string str = File.ReadAllText("Root.xml");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root>
                           <Child>child content</Child>
                       </Root>
root.Save("Root.xml")
Dim str As String = File.ReadAllText("Root.xml")
Console.WriteLine(str)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a>Örnek: XML bildirimi olmadan serileştirme

Aşağıdaki örnekte, bir ' a nasıl kaydedileceği gösterilmektedir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter> .

```csharp
StringBuilder sb = new StringBuilder();
XmlWriterSettings xws = new XmlWriterSettings();
xws.OmitXmlDeclaration = true;

using (XmlWriter xw = XmlWriter.Create(sb, xws)) {
    XElement root = new XElement("Root",
        new XElement("Child", "child content")
    );
    root.Save(xw);
}
Console.WriteLine(sb.ToString());
```

```vb
Dim sb As StringBuilder = New StringBuilder()
Dim xws As XmlWriterSettings = New XmlWriterSettings()
xws.OmitXmlDeclaration = True

Using xw As XmlWriter = XmlWriter.Create(sb, xws)
    Dim root = <Root>
                   <Child>child content</Child>
               </Root>
    root.Save(xw)
End Using
Console.WriteLine(sb.ToString())
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root><Child>child content</Child></Root>
```

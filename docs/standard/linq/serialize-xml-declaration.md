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
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a><span data-ttu-id="cb4a0-103">XML bildirimiyle serileştirme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cb4a0-103">Serialize with an XML declaration (LINQ to XML)</span></span>

<span data-ttu-id="cb4a0-104">Bu makalede, C# veya Visual Basic XML seri hale geldiğinde bir XML bildiriminin oluşturulup oluşturulmayacağını nasıl denetleyen açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cb4a0-104">This article describes how to control whether an XML declaration is generated when you serialize XML in C# or Visual Basic.</span></span>

<span data-ttu-id="cb4a0-105"><xref:System.IO.File>Yöntemini veya yöntemini kullanarak bir veya öğesine serileştirmek BIR <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb4a0-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="cb4a0-106">' A serileştirçalıştığınızda <xref:System.Xml.XmlWriter> , yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilir) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4a0-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated.</span></span>

<span data-ttu-id="cb4a0-107">Yöntemini kullanarak bir dizeye seri hale getiriyorsanız `ToString` , sonuçta elde EDILEN XML BIR XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="cb4a0-107">If you're serializing to a string using the `ToString` method, the resulting XML won't include an XML declaration.</span></span>

## <a name="example-serialize-with-an-xml-declaration"></a><span data-ttu-id="cb4a0-108">Örnek: bir XML bildirimiyle serileştirme</span><span class="sxs-lookup"><span data-stu-id="cb4a0-108">Example: Serialize with an XML declaration</span></span>

<span data-ttu-id="cb4a0-109">Aşağıdaki örnek bir dosyası oluşturur <xref:System.Xml.Linq.XElement> , belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="cb4a0-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>

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

<span data-ttu-id="cb4a0-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb4a0-110">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a><span data-ttu-id="cb4a0-111">Örnek: XML bildirimi olmadan serileştirme</span><span class="sxs-lookup"><span data-stu-id="cb4a0-111">Example: Serialize without an XML declaration</span></span>

<span data-ttu-id="cb4a0-112">Aşağıdaki örnekte, bir ' a nasıl kaydedileceği gösterilmektedir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="cb4a0-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>

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

<span data-ttu-id="cb4a0-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb4a0-113">This example produces the following output:</span></span>

```xml
<Root><Child>child content</Child></Root>
```

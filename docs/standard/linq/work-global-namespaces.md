---
title: Visual Basic LINQ to XML genel ad alanları ile çalışma
description: Ad alanının varsayılan bir ad alanı veya öneki olup olmadığı, Imports ifadesiyle Visual Basic bir ad alanı bildirirsiniz. Bu makalede Içeri aktarma deyimleri ve ad alanları ile çalışmanın diğer yönleri açıklanmaktadır.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553932"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a>Visual Basic genel ad alanları ile çalışma (LINQ to XML)

Visual Basic XML sabit değerlerinin temel özelliklerinden biri, ifadesini kullanarak XML ad alanları bildirme yeteneğidir `Imports` . Bu özelliği kullanarak, ön ek kullanan bir XML ad alanı bildirebilir veya varsayılan bir XML ad alanı bildirebilirsiniz.

Bu özellik iki durumda faydalıdır:

- XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz. Genel ad alanlarını bildirmek, katıştırılmış ifadeleri ad alanlarıyla birlikte kullanmak için gereken çalışma miktarını azaltır.
- XML özellikleriyle ad alanlarını kullanabilmeniz için genel ad alanlarını bildirmeniz gerekir.

Genel ad alanlarını proje düzeyinde bildirebilirsiniz. Genel ad alanlarını modül düzeyinde bildirebilirsiniz ve bu da proje düzeyi genel ad alanlarını geçersiz kılar. Son olarak, bir XML sabit değerinde genel ad alanlarını geçersiz kılabilirsiniz.

Genel olarak tanımlanan ad alanları içindeki XML değişmez değerlerini veya xml özelliklerini kullanırken, Visual Studio 'da üzerine giderek, XML değişmez değerlerinin veya özelliklerinin genişletilmiş adını görebilirsiniz. Genişletilmiş adı bir araç ipucunda görürsünüz.

<xref:System.Xml.Linq.XNamespace>Yöntemini kullanarak genel bir ad alanına karşılık gelen bir nesnesi alabilirsiniz `GetXmlNamespace` .

## <a name="example-use-imports-to-declare-a-global-namespace"></a>Örnek: `Imports` genel bir ad alanı bildirmek Için kullanın

Aşağıdaki örnek, ifadesiyle bir varsayılan genel ad alanı bildirir `Imports` ve ardından <xref:System.Xml.Linq.XElement> Bu ad alanındaki bir NESNEYI bir XML değişmez değeri ile başlatır:

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a>Örnek: ön eki olan genel bir ad alanı bildirin

Sonraki örnek, öneki olan bir genel ad alanı bildirir ve bir XML değişmez değeri olan bir öğe başlatır:

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a>Örnek: varsayılan bir ad alanı bildirin ve öğe için gömülü bir ifade kullanın `Child`

XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz. Aşağıdaki örnek bir varsayılan ad alanı bildirir ve ardından öğesi için gömülü bir ifade kullanır `Child` .

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

Elde edilen XML, bir varsayılan ad alanı bildirimi içerir, böylece `Child` öğe ad alanında yer alır.

Katıştırılmış ifadede aşağıdaki gibi farklı bir ad alanı bildirebilirsiniz:

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

Ancak, genel varsayılan ad alanı ile, ad alanlarını bildirmeden XML değişmez değerlerini kullanabilirsiniz. Elde edilen XML, bu örnekte olduğu gibi, genel olarak belirtilen varsayılan ad alanında olacaktır:

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a>Örnek: XML özellikleriyle ad alanlarını kullanma

Bir ad alanında olan bir XML ağacıyla çalışıyorsanız ve XML özelliklerini kullanıyorsanız, XML özelliklerinin de doğru ad alanında olması için genel bir ad alanı kullanmanız gerekir. Aşağıdaki örnek, bir ad alanında bir XML ağacını bildirir ve sonra öğe sayısını yazdırır `Child` .

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

Bu örnek, hiçbir öğe olmadığını gösterir `Child` . Bu çıktıyı oluşturur:

```output
0
```

Ancak, varsayılan bir genel ad alanı bildirirseniz, hem XML değişmez değeri hem de XML özelliği varsayılan genel ad alanında bulunur:

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

Bu örnek, bir öğe olduğunu gösterir `Child` . Bu çıktıyı oluşturur:

```output
1
```

Ön eki olan genel bir ad alanı bildirirseniz, öneki hem XML değişmez değerleri hem de XML özellikleri için kullanabilirsiniz:

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a>Örnek: şunu `GetXmlNamespace` almak Için kullanın `XNamespace`

<xref:System.Xml.Linq.XNamespace>Yöntemini kullanarak bir nesnesi elde edebilirsiniz `GetXmlNamespace` :

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
http://www.adventure-works.com
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış](namespaces-overview.md)

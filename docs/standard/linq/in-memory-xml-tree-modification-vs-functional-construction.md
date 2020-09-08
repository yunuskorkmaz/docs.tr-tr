---
title: Bellek içi XML ağacı değişikliği ile işlevsel oluşturma-LINQ to XML
description: XML ağaçlarını değiştirmenin iki farklı yaklaşımının örneklerine bakın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552973"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a>Bellek içi XML ağacı değişikliği ile işlevsel oluşturma (LINQ to XML)

Bir XML ağacını yerinde değiştirmek, bir XML belgesinin şeklini değiştirmenin geleneksel bir yaklaşımdır. Tipik bir uygulama, bir belgeyi DOM veya LINQ to XML gibi bir veri deposuna yükler; düğüm eklemek veya silmek ya da içeriklerini değiştirmek için bir programlama arabirimi kullanır; ardından, XML dosyasını bir dosyaya kaydeder veya ağ üzerinden iletir.

LINQ to XML, çok sayıda senaryoda faydalı olan başka bir yaklaşım sağlar: *işlevsel oluşturma*. İşlevsel oluşturma, verileri bir veri deposunun ayrıntılı olarak değiştirilmesi yerine dönüşümde bir sorun olarak değiştirir. Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebiliyorsanız, sonuç bir veri deposu alıp başka bir şekil almak için bir şekilde işleneceğinden aynı olur. İşlevsel oluşturma yaklaşımına bir anahtar, sorguların sonuçlarını <xref:System.Xml.Linq.XDocument> ve oluşturuculara geçirmektir <xref:System.Xml.Linq.XElement> .

Çoğu durumda, dönüştürme kodunu veri deposunun yönetilmesi için gereken sürenin bir bölümünde yazabilir ve sonuçta elde edilen kod daha sağlam ve daha kolay olur. Bu durumlarda, dönüştürme yaklaşımının daha fazla işlem gücü sürebilse de, verileri değiştirmek için daha etkili bir yoldur. Bir geliştirici işlevsel yaklaşımı öğrenir, çok sayıda durumda elde edilen kodun anlaşılması daha kolaydır ve ağacın her bölümünü değiştiren kodu kolayca bulabilirsiniz.

Yerinde bir XML ağacını değiştirdiğiniz yaklaşım birçok DOM programcısı için daha tanıdık gelecektir, ancak işlevsel yaklaşım kullanılarak yazılan kod, bu yaklaşımı henüz anlayamamış bir geliştiriciye tanıdık gelebilir. Büyük bir XML ağacında yalnızca küçük bir değişiklik yapmanız gerekiyorsa, bir ağacı birçok durumda değiştirdiğiniz yaklaşım daha az CPU süresi alır.

Bu makalede her iki yaklaşımdan örnekler sunulmaktadır. Aşağıdaki basit XML belgesini, özniteliklerin öğe olacak şekilde değiştirmek istediğinizi varsayalım:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

Aşağıdaki örneklerden ilki geleneksel yerinde değiştirme yaklaşımını kullanır ve ikincisi işlevsel oluşturma yaklaşımını kullanır.

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a>Örnek: geleneksel yerinde yaklaşımla öznitelikleri öğelere Dönüştür

Özniteliklerden öğe oluşturmak için bazı yordamsal kodlar yazabilir ve ardından aşağıdaki gibi öznitelikleri silebilirsiniz:

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a>Örnek: işlev oluşturma yaklaşımıyla öznitelikleri öğelere Dönüştür

Bunun aksine, işlevsel bir yaklaşım yeni bir ağaç oluşturacak, kaynak ağaçtan öğe ve öznitelik seçme, seçme ve bunları yeni ağaca eklendikçe uygun şekilde dönüştürme kodundan oluşur.

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

Bu örnek, ilk örnekle aynı XML 'e çıktı verir. Bununla birlikte, yeni XML 'nin ortaya çıkan yapısını işlevsel yaklaşımda görbildiğinize dikkat edin. `Root`Öğesinin oluşturulmasını, `Child1` kaynak ağacından öğeyi çeken kodu ve kaynak ağaç içindeki öznitelikleri yeni ağaç içindeki öğelere dönüştüren kodu görebilirsiniz.

Bu durumda işlevsel örnek, ilk örneğe göre daha kısa veya daha basit değildir. Ancak, bir XML ağacına yaptığınız birçok değişiklik varsa, yordamsal yaklaşım oldukça karmaşık ve biraz daha kolay hale gelir. Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için istenen XML 'yi, uygun şekilde ekleme sorgularını ve ifadeleri yazmanız yeterlidir. İşlevsel yaklaşım, bakımı daha kolay olan kodu verir.

Bu durumda, işlevsel yaklaşımın büyük olasılıkla ağaç işleme yaklaşımının çok iyi gerçekleştirmediğine dikkat edin. Ana sorun, işlevsel yaklaşımın daha kısa süreli nesneler oluşturmasıdır. Ancak, işlevsel yaklaşımın kullanılması daha fazla programcı verimliliğine izin veriyorsa zorunluluğunu getirir geçerli bir değer.

Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki FI 'teki farkı göstermek için kullanılır. İşlevsel yaklaşım, büyük XML belgelerini dönüştürmek için daha fazla verimlilik artışı sağlar.

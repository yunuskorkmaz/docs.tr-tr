---
title: Karma bildirime dayalı/zorunlu kod hataları-LINQ to XML
description: Bir eksen üzerinde değişiklikler yaparak oluşabilecek sorunları nasıl anlayacağınızı ve önleyeceğinizi öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553277"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a>Karma bildirime dayalı/zorunlu kod hataları (LINQ to XML)

LINQ to XML, bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir. Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz. Bu programlama arabirimi, [XML ağaçlarını değiştirme](in-memory-xml-tree-modification-vs-functional-construction.md)bölümünde açıklanmaktadır. Ve gibi eksenlerden birini yinelemenize sahipseniz <xref:System.Xml.Linq.XContainer.Elements%2A> ve eksen boyunca yineleme yaparken xml ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.

Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.

Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir. İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek daha fazla akkdır. 1) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır. Bilgisayara istediğiniz şeyi *nasıl* yapabileceğinizi söyleirsiniz.

Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir. Aşağıdaki topluluklara bir göz atın:

İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:

> a-> b-> c

Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım. Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:

 > a-> a '-> b-> b '-> c-> c '

Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler. Ne olacağı, kodunuzun öğeyi ilk göreceği `a` ve sonra ekleneceği şeydir `a'` . Şimdi, kodunuz listede bir sonraki düğüme taşınacak, bu `a'` nedenle listeye ' ve b arasına yeni bir öğe ekliyor!

Bunu nasıl çözeceğinizi? Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz. Ya da yalnızca zorunlu bir kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.

## <a name="example-adding-while-iterating"></a>Örnek: yineleme sırasında ekleme

Örneğin, bir ağaçtaki her öğenin Yineleneni oluşturmak için kod yazmak istediğinizi varsayalım:

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

Bu kod sonsuz bir döngüye girer. `foreach`İfade, `Elements()` öğesine yeni öğeler ekleyerek eksen boyunca yinelenir `doc` . Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer. Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.

Aşağıdaki gibi standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

Kod artık işe yarar. Elde edilen XML ağacı aşağıda verilmiştir:

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a>Örnek: yineleme sırasında silme

Tüm düğümleri belirli bir düzeyde silmek isterseniz, aşağıdaki gibi bir kod yazmayı düşünebilirsiniz:

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

Ancak, bu, istediğiniz şeyi yapmaz. Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod, bir sonraki öğeyi bulamaz.

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

Bu çözüm, <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu aşağıda gösterildiği gibi yeniden gerçekleştirmek için çağrmaktır:

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root />
```

Alternatif olarak, üst öğeyi çağırarak yinelemeyi tamamen ortadan kaldırabilirsiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> :

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a>Örnek: LINQ neden bu sorunları otomatik olarak işleyemez

Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır. Ancak, performans ve bellek kullanımı bakımından çok pahalıdır. Aslında, LINQ ve LINQ to XML bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.

Başka bir olası yaklaşım, bazı işlem sözdizimini LINQ 'a koymak ve derleyicinin, belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini tespit etmek için kodu analiz etmeyi denemesini sağlar. Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır. Aşağıdaki kodu inceleyin:

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir. Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı. Bu durumda yalnızca alt öğelerinde yan etkileri olan kod için seçim yapması gerekir `root` .

LINQ to XML böyle bir analiz yapmayı denemez. Bu sorunlardan kaçınmak için sizi kullanabilirsiniz.

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a>Örnek: varolan ağacı değiştirmek yerine yeni bir XML ağacı oluşturmak için bildirim temelli kod kullanın

Bu sorunlardan kaçınmak için, koleksiyonlarınızın anlamını ve XML ağacını değiştiren yöntemlerin semantiğini bilseniz bile, bildirim ve tanımlayıcı kodu karıştırmayın. Sorunları önleyen bir kod yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir ve sorunlar üzerinde açık olmayabilir. Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.  Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.

Performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın. Mevcut XML ağacınızı değiştirmeyin. Bunun yerine, aşağıdaki örnekte gösterildiği gibi yeni bir tane oluşturun:

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```

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
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a><span data-ttu-id="03606-103">Karma bildirime dayalı/zorunlu kod hataları (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="03606-103">Mixed declarative/imperative code bugs (LINQ to XML)</span></span>

<span data-ttu-id="03606-104">LINQ to XML, bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="03606-104">LINQ to XML contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="03606-105">Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-105">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="03606-106">Bu programlama arabirimi, [XML ağaçlarını değiştirme](in-memory-xml-tree-modification-vs-functional-construction.md)bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03606-106">This programming interface is described in [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span> <span data-ttu-id="03606-107">Ve gibi eksenlerden birini yinelemenize sahipseniz <xref:System.Xml.Linq.XContainer.Elements%2A> ve eksen boyunca yineleme yaparken xml ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-107">If you're iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you're modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>

<span data-ttu-id="03606-108">Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="03606-108">This problem is sometimes known as "The Halloween Problem".</span></span>

<span data-ttu-id="03606-109">Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir.</span><span class="sxs-lookup"><span data-stu-id="03606-109">When you write some code using LINQ that iterates through a collection, you're writing code in a declarative style.</span></span> <span data-ttu-id="03606-110">İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek daha fazla akkdır.</span><span class="sxs-lookup"><span data-stu-id="03606-110">It's more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="03606-111">1) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır.</span><span class="sxs-lookup"><span data-stu-id="03606-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="03606-112">Bilgisayara istediğiniz şeyi *nasıl* yapabileceğinizi söyleirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-112">You're telling the computer *how* to do what you want done.</span></span>

<span data-ttu-id="03606-113">Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="03606-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="03606-114">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="03606-114">Consider the following:</span></span>

<span data-ttu-id="03606-115">İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="03606-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>

> <span data-ttu-id="03606-116">a-> b-> c</span><span class="sxs-lookup"><span data-stu-id="03606-116">a -> b -> c</span></span>

<span data-ttu-id="03606-117">Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="03606-117">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="03606-118">Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="03606-118">You want the resulting linked list to look like this:</span></span>

 > <span data-ttu-id="03606-119">a-> a '-> b-> b '-> c-> c '</span><span class="sxs-lookup"><span data-stu-id="03606-119">a -> a' -> b -> b' -> c -> c'</span></span>

<span data-ttu-id="03606-120">Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="03606-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="03606-121">Ne olacağı, kodunuzun öğeyi ilk göreceği `a` ve sonra ekleneceği şeydir `a'` .</span><span class="sxs-lookup"><span data-stu-id="03606-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="03606-122">Şimdi, kodunuz listede bir sonraki düğüme taşınacak, bu `a'` nedenle listeye ' ve b arasına yeni bir öğe ekliyor!</span><span class="sxs-lookup"><span data-stu-id="03606-122">Now, your code will move to the next node in the list, which is now `a'`, so it adds a new item between a' and b to the list!</span></span>

<span data-ttu-id="03606-123">Bunu nasıl çözeceğinizi?</span><span class="sxs-lookup"><span data-stu-id="03606-123">How would you solve this?</span></span> <span data-ttu-id="03606-124">Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-124">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="03606-125">Ya da yalnızca zorunlu bir kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-125">Or if you're writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>

## <a name="example-adding-while-iterating"></a><span data-ttu-id="03606-126">Örnek: yineleme sırasında ekleme</span><span class="sxs-lookup"><span data-stu-id="03606-126">Example: Adding while iterating</span></span>

<span data-ttu-id="03606-127">Örneğin, bir ağaçtaki her öğenin Yineleneni oluşturmak için kod yazmak istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="03606-127">For example, suppose you want to write code to create a duplicate of every element in a tree:</span></span>

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

<span data-ttu-id="03606-128">Bu kod sonsuz bir döngüye girer.</span><span class="sxs-lookup"><span data-stu-id="03606-128">This code goes into an infinite loop.</span></span> <span data-ttu-id="03606-129">`foreach`İfade, `Elements()` öğesine yeni öğeler ekleyerek eksen boyunca yinelenir `doc` .</span><span class="sxs-lookup"><span data-stu-id="03606-129">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="03606-130">Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="03606-130">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="03606-131">Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.</span><span class="sxs-lookup"><span data-stu-id="03606-131">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>

<span data-ttu-id="03606-132">Aşağıdaki gibi standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> :</span><span class="sxs-lookup"><span data-stu-id="03606-132">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>

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

<span data-ttu-id="03606-133">Kod artık işe yarar.</span><span class="sxs-lookup"><span data-stu-id="03606-133">Now the code works.</span></span> <span data-ttu-id="03606-134">Elde edilen XML ağacı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="03606-134">The resulting XML tree is the following:</span></span>

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

## <a name="example-deleting-while-iterating"></a><span data-ttu-id="03606-135">Örnek: yineleme sırasında silme</span><span class="sxs-lookup"><span data-stu-id="03606-135">Example: Deleting while iterating</span></span>

<span data-ttu-id="03606-136">Tüm düğümleri belirli bir düzeyde silmek isterseniz, aşağıdaki gibi bir kod yazmayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="03606-136">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>

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

<span data-ttu-id="03606-137">Ancak, bu, istediğiniz şeyi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="03606-137">However, this doesn't do what you want.</span></span> <span data-ttu-id="03606-138">Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod, bir sonraki öğeyi bulamaz.</span><span class="sxs-lookup"><span data-stu-id="03606-138">In this situation, after you've removed the first element, A, it's removed from the XML tree contained in root, and the code in the Elements method that does the iterating can't find the next element.</span></span>

<span data-ttu-id="03606-139">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="03606-139">This example produces the following output:</span></span>

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

<span data-ttu-id="03606-140">Bu çözüm, <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu aşağıda gösterildiği gibi yeniden gerçekleştirmek için çağrmaktır:</span><span class="sxs-lookup"><span data-stu-id="03606-140">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>

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

<span data-ttu-id="03606-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="03606-141">This example produces the following output:</span></span>

```xml
<Root />
```

<span data-ttu-id="03606-142">Alternatif olarak, üst öğeyi çağırarak yinelemeyi tamamen ortadan kaldırabilirsiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> :</span><span class="sxs-lookup"><span data-stu-id="03606-142">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>

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

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a><span data-ttu-id="03606-143">Örnek: LINQ neden bu sorunları otomatik olarak işleyemez</span><span class="sxs-lookup"><span data-stu-id="03606-143">Example: Why LINQ can't automatically handle these issues</span></span>

<span data-ttu-id="03606-144">Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="03606-144">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="03606-145">Ancak, performans ve bellek kullanımı bakımından çok pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="03606-145">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="03606-146">Aslında, LINQ ve LINQ to XML bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="03606-146">In fact, if LINQ, and LINQ to XML, were to take this approach, it would fail in real-world situations.</span></span>

<span data-ttu-id="03606-147">Başka bir olası yaklaşım, bazı işlem sözdizimini LINQ 'a koymak ve derleyicinin, belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini tespit etmek için kodu analiz etmeyi denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="03606-147">Another possible approach would be to put some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code to determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="03606-148">Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="03606-148">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="03606-149">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="03606-149">Consider the following code:</span></span>

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

<span data-ttu-id="03606-150">Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="03606-150">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="03606-151">Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı.</span><span class="sxs-lookup"><span data-stu-id="03606-151">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="03606-152">Bu durumda yalnızca alt öğelerinde yan etkileri olan kod için seçim yapması gerekir `root` .</span><span class="sxs-lookup"><span data-stu-id="03606-152">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>

<span data-ttu-id="03606-153">LINQ to XML böyle bir analiz yapmayı denemez.</span><span class="sxs-lookup"><span data-stu-id="03606-153">LINQ to XML doesn't attempt to do any such analysis.</span></span> <span data-ttu-id="03606-154">Bu sorunlardan kaçınmak için sizi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-154">It's up to you to avoid these problems.</span></span>

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a><span data-ttu-id="03606-155">Örnek: varolan ağacı değiştirmek yerine yeni bir XML ağacı oluşturmak için bildirim temelli kod kullanın</span><span class="sxs-lookup"><span data-stu-id="03606-155">Example: Use declarative code to generate a new XML tree rather than modify the existing tree</span></span>

<span data-ttu-id="03606-156">Bu sorunlardan kaçınmak için, koleksiyonlarınızın anlamını ve XML ağacını değiştiren yöntemlerin semantiğini bilseniz bile, bildirim ve tanımlayıcı kodu karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="03606-156">To avoid such problems, don't mix declarative and imperative code, even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree.</span></span> <span data-ttu-id="03606-157">Sorunları önleyen bir kod yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir ve sorunlar üzerinde açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="03606-157">If you write code that avoids problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="03606-158">Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="03606-158">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  <span data-ttu-id="03606-159">Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03606-159">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>

<span data-ttu-id="03606-160">Performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="03606-160">If performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="03606-161">Mevcut XML ağacınızı değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="03606-161">Don't modify your existing XML tree.</span></span> <span data-ttu-id="03606-162">Bunun yerine, aşağıdaki örnekte gösterildiği gibi yeni bir tane oluşturun:</span><span class="sxs-lookup"><span data-stu-id="03606-162">Instead, generate a new one as shown in the following example:</span></span>

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

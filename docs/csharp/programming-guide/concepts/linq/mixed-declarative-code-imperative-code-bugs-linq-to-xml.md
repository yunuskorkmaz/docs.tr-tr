---
title: Karışık Bildirimkod-Zorunlu Kod Hataları (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 76a9bb5abf6ce2700a2a0698ebc109f65e2b7eb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168355"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="e76d5-102">Karışık Bildirim kodu/Zorunlu Kod Hataları (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e76d5-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e76d5-103">doğrudan bir XML ağacını değiştirmenize olanak tanıyan çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="e76d5-104">Öğeler ekleyebilir, öğeleri silebilir, öğenin içeriğini değiştirebilir, öznitelikler ekleyebilirsiniz ve benzeri şeyler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="e76d5-105">Bu programlama [arabirimi, XML Ağaçlarını Değiştirme (LINQ - XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="e76d5-106">Eksenlerden <xref:System.Xml.Linq.XContainer.Elements%2A>birini yinelerseniz ve eksen boyunca yinelerken XML ağacını değiştiriyorsanız, bazı garip hatalarla başa çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="e76d5-107">Bu sorun bazen "Cadılar Bayramı Sorunu" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="e76d5-108">Sorunun Tanımı</span><span class="sxs-lookup"><span data-stu-id="e76d5-108">Definition of the Problem</span></span>  
 <span data-ttu-id="e76d5-109">LinQ kullanarak bir koleksiyon aracılığıyla yineleyen bazı kodlar yazdığınızda, kodbildirimel bir biçimde yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="e76d5-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="e76d5-110">Bu daha çok *ne* istediğinizi açıklamaya benzer, daha çok *nasıl* yapmak istediğinizi.</span><span class="sxs-lookup"><span data-stu-id="e76d5-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="e76d5-111">Eğer kod yazarsanız 1) ilk öğealır, 2) bazı koşullar için test, 3) değiştirir ve 4) listeye geri koyar, o zaman bu zorunlu kod olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="e76d5-112">Bilgisayara yapılmasını istediğin şeyi *nasıl* yapacağını söylüyorsun.</span><span class="sxs-lookup"><span data-stu-id="e76d5-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="e76d5-113">Bu kod stillerini aynı işlemde karıştırmak sorunlara yol açar.</span><span class="sxs-lookup"><span data-stu-id="e76d5-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="e76d5-114">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="e76d5-114">Consider the following:</span></span>  
  
 <span data-ttu-id="e76d5-115">Içinde üç öğe (a, b ve c) bulunan bağlantılı bir listenizle varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e76d5-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="e76d5-116">Şimdi, üç yeni öğe (a', b', ve c') ekleyerek bağlantılı listede taşımak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e76d5-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="e76d5-117">Ortaya çıkan bağlantılı listenin şuna benzemesini istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="e76d5-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="e76d5-118">Bu nedenle, liste boyunca yineleyen bir kod yazarsınız ve her öğe için hemen sonra yeni bir öğe eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="e76d5-119">Ne olur, kodunuzu ilk `a` öğeyi görmek `a'` ve ondan sonra eklemek olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="e76d5-120">Şimdi, kodunuz listedeki bir sonraki düğüme `a'`geçecek, şimdi!</span><span class="sxs-lookup"><span data-stu-id="e76d5-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="e76d5-121">Bu mutlu listeye yeni bir öğe `a''`ekler.</span><span class="sxs-lookup"><span data-stu-id="e76d5-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="e76d5-122">Bunu gerçek dünyada nasıl çözersin?</span><span class="sxs-lookup"><span data-stu-id="e76d5-122">How would you solve this in the real world?</span></span> <span data-ttu-id="e76d5-123">Orijinal bağlantılı listenin bir kopyasını oluşturup tamamen yeni bir liste oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="e76d5-124">Veya tamamen zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve bağlı listede iki kez ilerleyerek eklediğiniz öğenin üzerinde ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="e76d5-125">Yinelerken Ekleme</span><span class="sxs-lookup"><span data-stu-id="e76d5-125">Adding While Iterating</span></span>  
 <span data-ttu-id="e76d5-126">Örneğin, bir ağaçtaki her öğe için yinelenen bir öğe oluşturmak istediğiniz bazı kodlar yazmak istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e76d5-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="e76d5-127">Bu kod sonsuz bir döngüye girer.</span><span class="sxs-lookup"><span data-stu-id="e76d5-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="e76d5-128">İfade `foreach` `Elements()` eksen üzerinden yineler ve `doc` öğeye yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="e76d5-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="e76d5-129">Sadece ekleyen öğeler aracılığıyla da yineler.</span><span class="sxs-lookup"><span data-stu-id="e76d5-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="e76d5-130">Ve döngünün her yinelemeile yeni nesneler ayırdığı için, sonunda kullanılabilir tüm belleği tüketir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="e76d5-131">Aşağıdaki <xref:System.Linq.Enumerable.ToList%2A> gibi, standart sorgu işleci kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e76d5-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="e76d5-132">Şimdi kod çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="e76d5-132">Now the code works.</span></span> <span data-ttu-id="e76d5-133">Ortaya çıkan XML ağacı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e76d5-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="e76d5-134">Yineleme sırasında silme</span><span class="sxs-lookup"><span data-stu-id="e76d5-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="e76d5-135">Belirli bir düzeydeki tüm düğümleri silmek istiyorsanız, aşağıdaki gibi kod yazmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e76d5-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="e76d5-136">Ancak, bu ne istediğinizi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-136">However, this does not do what you want.</span></span> <span data-ttu-id="e76d5-137">Bu durumda, ilk öğeyi kaldırdıktan sonra, A, kökte bulunan XML ağacından kaldırılır ve yineleyen öğeler yöntemindeki kod sonraki öğeyi bulamaz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="e76d5-138">Önceki kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e76d5-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="e76d5-139">Çözüm yine aşağıdaki <xref:System.Linq.Enumerable.ToList%2A> gibi, koleksiyonu hayata getirmek için aramaktır:</span><span class="sxs-lookup"><span data-stu-id="e76d5-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="e76d5-140">Bu, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e76d5-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="e76d5-141">Alternatif olarak, üst öğeyi çağırarak <xref:System.Xml.Linq.XElement.RemoveAll%2A> yinelemeyi tamamen ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e76d5-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="e76d5-142">LINQ Neden Bunu Otomatik Olarak İşletemez?</span><span class="sxs-lookup"><span data-stu-id="e76d5-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="e76d5-143">Bir yaklaşım her zaman yerine tembel değerlendirme yapıyor bellek her şeyi getirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="e76d5-144">Ancak, performans ve bellek kullanımı açısından çok pahalı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="e76d5-145">Aslında, LINQ ve (LINQ XML için) bu yaklaşımı almak olsaydı, gerçek dünya durumlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e76d5-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="e76d5-146">Başka bir olası yaklaşım LINQ içine işlem sözdizimi çeşit koymak ve derleyici kodu analiz etmek ve belirli bir koleksiyon gerçekleştirilmesi için gerekli olup olmadığını belirlemek için girişimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="e76d5-147">Ancak, yan etkileri olan tüm kodu belirlemeye çalışmak inanılmaz derecede karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="e76d5-148">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="e76d5-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="e76d5-149">Bu tür analiz kodu yöntemleri TestSomeCondition ve DoMyProjection ve bu yöntemler in called tüm yöntemleri, herhangi bir kod yan etkileri olup olmadığını belirlemek için analiz etmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="e76d5-150">Ama analiz kodu sadece yan etkileri olan herhangi bir kod aramak olamazdı.</span><span class="sxs-lookup"><span data-stu-id="e76d5-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="e76d5-151">Bu durumda alt öğeleri `root` üzerinde yan etkileri vardı sadece kod için seçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="e76d5-152">LINQ xml için böyle bir analiz yapmaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e76d5-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="e76d5-153">Bu sorunlardan kaçınmak size kalmış.</span><span class="sxs-lookup"><span data-stu-id="e76d5-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="e76d5-154">Rehber</span><span class="sxs-lookup"><span data-stu-id="e76d5-154">Guidance</span></span>  
 <span data-ttu-id="e76d5-155">İlk olarak, bildirimsel ve zorunlu kodu karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="e76d5-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="e76d5-156">Koleksiyonlarınızın anlambilimini ve XML ağacını değiştiren yöntemlerin anlambilimini tam olarak biliyor olsanız bile, bu sorun kategorilerinden kaçınan bazı akıllı kodlar yazarsanız, kodunuzu gelecekte diğer geliştiriciler tarafından muhafaza edilmesi gerekir ve bu konularda o kadar açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e76d5-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="e76d5-157">Bildirimsel ve zorunlu kodlama stillerini karıştırırsanız, kodunuz daha kırılgan olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e76d5-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="e76d5-158">Bu sorunların önlenebilecek şekilde bir koleksiyonu somutlaştıran bir kod yazarsanız, bakım programcılarının sorunu anlaması için bunu kodunuzda uygun açıklamalarla not edin.</span><span class="sxs-lookup"><span data-stu-id="e76d5-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="e76d5-159">İkinci olarak, performans ve diğer hususlar izin verirse, yalnızca bildirim kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e76d5-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="e76d5-160">Varolan XML ağacınızı değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="e76d5-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="e76d5-161">Yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e76d5-161">Generate a new one.</span></span>  
  
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

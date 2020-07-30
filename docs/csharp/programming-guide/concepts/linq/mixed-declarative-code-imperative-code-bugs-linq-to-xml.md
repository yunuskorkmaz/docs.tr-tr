---
title: Karma bildirime dayalı kod-zorunlu kod hataları (LINQ to XML) (C#)
description: LINQ to XML Yöntemler, doğrudan bir XML ağacını değiştirebilir. XML ağacını değiştirirken eksenlerden birinde yineleme, tek hatalara izin verebilir.
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 4eaed10f0a2e64abeb7725dcd70816d75d8a0423
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165286"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="82feb-104">Karma bildirime dayalı kod/zorunlu kod hataları (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="82feb-104">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="82feb-105">bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="82feb-105">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="82feb-106">Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-106">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="82feb-107">Bu programlama arabirimi, [XML ağaçlarını (LINQ to XML) (C#) değiştirme](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)konusunda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82feb-107">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="82feb-108">Ve gibi eksenlerden birini yinelemenize sahipseniz <xref:System.Xml.Linq.XContainer.Elements%2A> ve eksen boyunca yineleme yaparken xml ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-108">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="82feb-109">Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="82feb-109">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="82feb-110">Sorunun tanımı</span><span class="sxs-lookup"><span data-stu-id="82feb-110">Definition of the Problem</span></span>  
 <span data-ttu-id="82feb-111">Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir.</span><span class="sxs-lookup"><span data-stu-id="82feb-111">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="82feb-112">İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek için daha fazla oturum vardır.</span><span class="sxs-lookup"><span data-stu-id="82feb-112">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="82feb-113">1) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır.</span><span class="sxs-lookup"><span data-stu-id="82feb-113">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="82feb-114">*Bilgisayara ne yapılacağını istediğinizi* söyleirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-114">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="82feb-115">Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="82feb-115">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="82feb-116">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="82feb-116">Consider the following:</span></span>  
  
 <span data-ttu-id="82feb-117">İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="82feb-117">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="82feb-118">Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="82feb-118">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="82feb-119">Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="82feb-119">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="82feb-120">Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="82feb-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="82feb-121">Ne olacağı, kodunuzun öğeyi ilk göreceği `a` ve sonra ekleneceği şeydir `a'` .</span><span class="sxs-lookup"><span data-stu-id="82feb-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="82feb-122">Şimdi, kodunuz listede bir sonraki düğüme geçmeyecektir. `a'`</span><span class="sxs-lookup"><span data-stu-id="82feb-122">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="82feb-123">Bu, listeye yeni bir öğe ekler `a''` .</span><span class="sxs-lookup"><span data-stu-id="82feb-123">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="82feb-124">Bunu gerçek dünyada nasıl çözirsiniz?</span><span class="sxs-lookup"><span data-stu-id="82feb-124">How would you solve this in the real world?</span></span> <span data-ttu-id="82feb-125">Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-125">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="82feb-126">Ya da yalnızca zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-126">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="82feb-127">Yineleme sırasında ekleme</span><span class="sxs-lookup"><span data-stu-id="82feb-127">Adding While Iterating</span></span>  
 <span data-ttu-id="82feb-128">Örneğin, bir ağaçtaki her öğe için bir kod yazmak istediğinizi, yinelenen bir öğe oluşturmak istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="82feb-128">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="82feb-129">Bu kod sonsuz bir döngüye girer.</span><span class="sxs-lookup"><span data-stu-id="82feb-129">This code goes into an infinite loop.</span></span> <span data-ttu-id="82feb-130">`foreach`İfade, `Elements()` öğesine yeni öğeler ekleyerek eksen boyunca yinelenir `doc` .</span><span class="sxs-lookup"><span data-stu-id="82feb-130">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="82feb-131">Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="82feb-131">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="82feb-132">Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.</span><span class="sxs-lookup"><span data-stu-id="82feb-132">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="82feb-133">Aşağıdaki gibi standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> :</span><span class="sxs-lookup"><span data-stu-id="82feb-133">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="82feb-134">Kod artık işe yarar.</span><span class="sxs-lookup"><span data-stu-id="82feb-134">Now the code works.</span></span> <span data-ttu-id="82feb-135">Elde edilen XML ağacı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="82feb-135">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="82feb-136">Yineleme sırasında silme</span><span class="sxs-lookup"><span data-stu-id="82feb-136">Deleting While Iterating</span></span>  
 <span data-ttu-id="82feb-137">Tüm düğümleri belirli bir düzeyde silmek isterseniz, aşağıdaki gibi bir kod yazmayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="82feb-137">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="82feb-138">Ancak, bu, istediğiniz şeyi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="82feb-138">However, this does not do what you want.</span></span> <span data-ttu-id="82feb-139">Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod bir sonraki öğeyi bulamaz.</span><span class="sxs-lookup"><span data-stu-id="82feb-139">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="82feb-140">Yukarıdaki kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="82feb-140">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="82feb-141">Bu çözüm, <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu aşağıda gösterildiği gibi yeniden gerçekleştirmek için çağrmaktır:</span><span class="sxs-lookup"><span data-stu-id="82feb-141">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="82feb-142">Bu, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="82feb-142">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="82feb-143">Alternatif olarak, üst öğeyi çağırarak yinelemeyi tamamen ortadan kaldırabilirsiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> :</span><span class="sxs-lookup"><span data-stu-id="82feb-143">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="82feb-144">LINQ neden bunu otomatik olarak Işleyemiyor?</span><span class="sxs-lookup"><span data-stu-id="82feb-144">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="82feb-145">Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="82feb-145">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="82feb-146">Ancak, performans ve bellek kullanımı bakımından çok pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="82feb-146">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="82feb-147">Aslında, LINQ ve (LINQ to XML) bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="82feb-147">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="82feb-148">Başka bir olası yaklaşım, bazı işlem söz dizimine LINQ 'a yerleştirilecek ve derleyicinin kodu analiz etmeyi denemesini ve belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini belirleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82feb-148">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="82feb-149">Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="82feb-149">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="82feb-150">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="82feb-150">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="82feb-151">Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82feb-151">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="82feb-152">Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı.</span><span class="sxs-lookup"><span data-stu-id="82feb-152">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="82feb-153">Bu durumda yalnızca alt öğelerinde yan etkileri olan kod için seçim yapması gerekir `root` .</span><span class="sxs-lookup"><span data-stu-id="82feb-153">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="82feb-154">LINQ to XML böyle bir analiz yapmayı denemez.</span><span class="sxs-lookup"><span data-stu-id="82feb-154">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="82feb-155">Bu sorunlardan kaçınmak sizin için.</span><span class="sxs-lookup"><span data-stu-id="82feb-155">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="82feb-156">Rehber</span><span class="sxs-lookup"><span data-stu-id="82feb-156">Guidance</span></span>  
 <span data-ttu-id="82feb-157">İlk olarak, bildirim temelli ve kesinlik temelli kodu karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="82feb-157">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="82feb-158">Koleksiyonlarınızın semantiğini ve xml ağacını değiştiren yöntemlerin semantiğini bildiğiniz halde, bu sorun kategorilerini engelleyen bazı zekice kodu yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir ve sorunlar üzerinde net bir şekilde bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="82feb-158">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="82feb-159">Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="82feb-159">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="82feb-160">Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82feb-160">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="82feb-161">İkincisi, performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="82feb-161">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="82feb-162">Mevcut XML ağacınızı değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="82feb-162">Don't modify your existing XML tree.</span></span> <span data-ttu-id="82feb-163">Yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82feb-163">Generate a new one.</span></span>  
  
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

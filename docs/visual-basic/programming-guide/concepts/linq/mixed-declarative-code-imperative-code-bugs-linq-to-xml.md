---
title: Bildirim Temelli-Kesinlik Temelli Kod Hataları Karışımı (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: 369fae59516df785ac686645d47e74e69a8f1457
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331655"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="df953-102">Karma bildirime dayalı kod/zorunlu kod hataları (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df953-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="df953-103">, bir XML ağacını doğrudan değiştirmenize olanak sağlayan çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="df953-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="df953-104">Öğe ekleyebilir, öğeleri silebilir, bir öğenin içeriğini değiştirebilir, öznitelik ekleyebilir ve benzerlerini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="df953-105">Bu programlama arabirimi, [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df953-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="df953-106"><xref:System.Xml.Linq.XContainer.Elements%2A>gibi eksenlerden birini yinelemenize ve eksen boyunca yineleme yaparken XML ağacını değiştiriyorsanız, bazı garip hatalara sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="df953-107">Bu sorun bazen "Cadılar Bayramı sorunu" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="df953-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="df953-108">Sorunun tanımı</span><span class="sxs-lookup"><span data-stu-id="df953-108">Definition of the Problem</span></span>  
 <span data-ttu-id="df953-109">Bir koleksiyon aracılığıyla yinelenen LINQ kullanarak bazı kodlar yazdığınızda, bildirime dayalı bir stilde kod yazıyor demektir.</span><span class="sxs-lookup"><span data-stu-id="df953-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="df953-110">İstediğiniz *şeyi* açıklamak, bunun yerine *nasıl* yapılacağını öğrenmek için daha fazla oturum vardır.</span><span class="sxs-lookup"><span data-stu-id="df953-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="df953-111">1\) ilk öğeyi alan bir kod yazarsanız, 2) onu bir koşul için sınar, 3) onu değiştirir ve 4) listeye geri koyar, bu da zorunlu kod olacaktır.</span><span class="sxs-lookup"><span data-stu-id="df953-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="df953-112">*Bilgisayara ne yapılacağını istediğinizi* söyleirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="df953-113">Bu kod stillerinin aynı işlemde karıştırılması, sorunlara yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="df953-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="df953-114">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="df953-114">Consider the following:</span></span>  
  
 <span data-ttu-id="df953-115">İçinde üç öğe (a, b ve c) içeren bağlı bir listeniz olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="df953-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="df953-116">Şimdi, bağlantılı liste içinde, üç yeni öğe (', b ' ve c ') ekleyerek geçiş yapmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="df953-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="df953-117">Elde edilen bağlantılı listenin şuna benzer görünmesini istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="df953-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="df953-118">Bu nedenle, liste boyunca yinelenen kod yazdığınızda ve her öğe için, hemen sonrasında yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="df953-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="df953-119">Ne olur, kodunuzun `a` öğeyi ilk göreceği ve sonra `a'` eklemesi.</span><span class="sxs-lookup"><span data-stu-id="df953-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="df953-120">Şimdi, kodunuz listede bir sonraki düğüme geçmeyecektir. bu `a'`!</span><span class="sxs-lookup"><span data-stu-id="df953-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="df953-121">`a''`listeye yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="df953-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="df953-122">Bunu gerçek dünyada nasıl çözirsiniz?</span><span class="sxs-lookup"><span data-stu-id="df953-122">How would you solve this in the real world?</span></span> <span data-ttu-id="df953-123">Ayrıca, özgün bağlantılı listenin bir kopyasını oluşturabilir ve tamamen yeni bir liste oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="df953-124">Ya da yalnızca zorunlu kod yazıyorsanız, ilk öğeyi bulabilir, yeni öğeyi ekleyebilir ve ardından bağlantılı listede iki kez ilerledikten sonra yeni eklediğiniz öğeden ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="df953-125">Yineleme sırasında ekleme</span><span class="sxs-lookup"><span data-stu-id="df953-125">Adding While Iterating</span></span>  
 <span data-ttu-id="df953-126">Örneğin, bir ağaçtaki her öğe için bir kod yazmak istediğinizi, yinelenen bir öğe oluşturmak istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="df953-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
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
  
 <span data-ttu-id="df953-127">Bu kod sonsuz bir döngüye girer.</span><span class="sxs-lookup"><span data-stu-id="df953-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="df953-128">`foreach` ifade, `doc` öğesine yeni öğeler ekleyerek `Elements()` eksen boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="df953-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="df953-129">Aynı zamanda, yeni eklenen öğeler aracılığıyla yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="df953-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="df953-130">Ayrıca, döngünün her tekrarında yeni nesneler ayırdığından, son olarak tüm kullanılabilir belleği tüketir.</span><span class="sxs-lookup"><span data-stu-id="df953-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="df953-131">Aşağıdaki gibi <xref:System.Linq.Enumerable.ToList%2A> standart sorgu işlecini kullanarak koleksiyonu belleğe çekerek bu sorunu çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df953-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="df953-132">Kod artık işe yarar.</span><span class="sxs-lookup"><span data-stu-id="df953-132">Now the code works.</span></span> <span data-ttu-id="df953-133">Elde edilen XML ağacı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="df953-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="df953-134">Yineleme sırasında silme</span><span class="sxs-lookup"><span data-stu-id="df953-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="df953-135">Tüm düğümleri belirli bir düzeyde silmek isterseniz, aşağıdaki gibi bir kod yazmayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df953-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="df953-136">Ancak, bu, istediğiniz şeyi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="df953-136">However, this does not do what you want.</span></span> <span data-ttu-id="df953-137">Bu durumda, ilk öğesini kaldırıldıktan sonra, bir, kök içinde yer alan XML ağacından kaldırılır ve yineleme yapan öğeler yöntemindeki kod bir sonraki öğeyi bulamaz.</span><span class="sxs-lookup"><span data-stu-id="df953-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="df953-138">Yukarıdaki kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="df953-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="df953-139">Çözüm, aşağıdaki gibi, koleksiyonu gerçekleştirmek için <xref:System.Linq.Enumerable.ToList%2A> çağırmaktır:</span><span class="sxs-lookup"><span data-stu-id="df953-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="df953-140">Bu, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="df953-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="df953-141">Alternatif olarak, üst öğedeki <xref:System.Xml.Linq.XElement.RemoveAll%2A> çağırarak yinelemeyi tamamen ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df953-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="df953-142">LINQ neden bunu otomatik olarak Işleyemiyor?</span><span class="sxs-lookup"><span data-stu-id="df953-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="df953-143">Tek bir yaklaşım, her şeyi yavaş değerlendirme yapmak yerine her zaman belleğe getirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="df953-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="df953-144">Ancak, performans ve bellek kullanımı bakımından çok pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="df953-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="df953-145">Aslında, LINQ ve (LINQ to XML) bu yaklaşıma ulaşacaksa, gerçek dünyada durumlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="df953-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="df953-146">Başka bir olası yaklaşım, bazı işlem söz dizimine LINQ 'a yerleştirilecek ve derleyicinin kodu analiz etmeyi denemesini ve belirli bir koleksiyonun gerçekleştirilip gerçekleştirilmeyeceğini belirleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="df953-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="df953-147">Ancak, yan etkileri olan tüm kodları belirleme girişimi inanılmaz karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="df953-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="df953-148">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="df953-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="df953-149">Bu tür analiz kodu, herhangi bir kodun yan etkilere sahip olup olmadığını anlamak için TestSomeCondition ve DoMyProjection yöntemlerini ve bu yöntemlerin çağırdığı tüm yöntemleri analiz etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="df953-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="df953-150">Ancak, analiz kodu yalnızca yan etkileri olan herhangi bir koda bakamadı.</span><span class="sxs-lookup"><span data-stu-id="df953-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="df953-151">Bu durumda `root` alt öğelerinde yalnızca yan etkileri olan kod için seçim yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="df953-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="df953-152">LINQ to XML böyle bir analiz yapmayı denemez.</span><span class="sxs-lookup"><span data-stu-id="df953-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="df953-153">Bu sorunlardan kaçınmak sizin için.</span><span class="sxs-lookup"><span data-stu-id="df953-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="df953-154">Rehber</span><span class="sxs-lookup"><span data-stu-id="df953-154">Guidance</span></span>  
 <span data-ttu-id="df953-155">İlk olarak, bildirim temelli ve kesinlik temelli kodu karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="df953-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="df953-156">Koleksiyonlarınızın semantiğini ve xml ağacını değiştiren yöntemlerin semantiğini bildiğiniz halde, bu sorun kategorilerini engelleyen bazı zekice kodu yazarsanız, kodunuzun gelecekte diğer geliştiriciler tarafından tutulması gerekir , ve sorunlar üzerinde açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="df953-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="df953-157">Bildirime dayalı ve kesinlik temelli kodlama stillerini karıştırırsanız, kodunuz daha Brittle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="df953-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="df953-158">Bu sorunların kaçınılması için bir koleksiyonu üreten bir kod yazarsanız, bakım programcılarının sorunu anlayabilmesi için kodunuzda uygun olan açıklamalara göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df953-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="df953-159">İkincisi, performans ve diğer hususlar izin veriyor ise yalnızca bildirim temelli kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="df953-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="df953-160">Mevcut XML ağacınızı değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="df953-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="df953-161">Yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="df953-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df953-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df953-162">See also</span></span>

- [<span data-ttu-id="df953-163">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df953-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

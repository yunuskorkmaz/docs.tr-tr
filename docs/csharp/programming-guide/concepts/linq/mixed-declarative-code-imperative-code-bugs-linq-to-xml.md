---
title: Bildirim temelli kod-kesinlik temelli kod hataları (LINQ to XML) karışık (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 5963e470acebfe259126ab8f2a17e131cb44f25b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682397"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="fa075-102">Bildirim temelli kod/kesinliği kod hataları karışımı (LINQ to XML) karışık (C#)</span><span class="sxs-lookup"><span data-stu-id="fa075-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fa075-103">bir XML ağacı doğrudan değiştirmenize olanak tanıyan çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="fa075-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="fa075-104">Öğeleri ekleyebilir, öğeleri silin, bir öğenin içeriğini değiştirme, öznitelikleri ekleme ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="fa075-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="fa075-105">Bu programlama arabirimi açıklanan [XML ağaçlarını değiştirme (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fa075-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="fa075-106">Bir eksen gibi yineleme, <xref:System.Xml.Linq.XContainer.Elements%2A>ve eksen yineleme gibi XML ağacı değiştirmekte olduğunuz, garip bazı hatalarla kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa075-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="fa075-107">Bu sorun, bazen "Cadılar Bayramı sorunu" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="fa075-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="fa075-108">Sorun tanımı</span><span class="sxs-lookup"><span data-stu-id="fa075-108">Definition of the Problem</span></span>  
 <span data-ttu-id="fa075-109">Bir koleksiyonda tekrarlanan LINQ kullanarak biraz kod yazdığınızda, bildirim temelli bir stilde kodu yazıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="fa075-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="fa075-110">Daha fazla açıklayan yakındır *ne* istediğiniz, bunun yerine, *nasıl* bitti almak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="fa075-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="fa075-111">(1) ilk öğeyi alır bir kod yazarsanız, bu kesinlik temelli kod şu şekilde olacaktır (2) testler bazı koşullar için 3) bunu değiştirir ve 4) bunu koyar listesine yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa075-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="fa075-112">Bilgisayar söylüyoruz *nasıl* bitti istediğiniz yapmak için.</span><span class="sxs-lookup"><span data-stu-id="fa075-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="fa075-113">Kod aynı işlemde bu stiller karıştırma ne sorunlar müşteri adayları olur.</span><span class="sxs-lookup"><span data-stu-id="fa075-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="fa075-114">Aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fa075-114">Consider the following:</span></span>  
  
 <span data-ttu-id="fa075-115">Üç öğe ile bağlı bir liste içinde olduğunu varsayalım (a, b ve c):</span><span class="sxs-lookup"><span data-stu-id="fa075-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="fa075-116">Şimdi, bağlantılı listesinde taşımak üç yeni öğeler eklemek istediğiniz varsayalım (bir ', b' ve c').</span><span class="sxs-lookup"><span data-stu-id="fa075-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="fa075-117">Sonuçta elde edilen bağlantılı liste gibi görünecek şekilde istediğiniz:</span><span class="sxs-lookup"><span data-stu-id="fa075-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="fa075-118">Bu nedenle listesinde ve her öğe için yineler kod yazma yeni bir öğeyi sağ sonra ekler.</span><span class="sxs-lookup"><span data-stu-id="fa075-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="fa075-119">Kodunuzu ilk Seti görecek olmasıdır ne `a` öğesi ve ekleme `a'` sonraki.</span><span class="sxs-lookup"><span data-stu-id="fa075-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="fa075-120">Artık, kodunuz artık listesinde sonraki düğüme taşır `a'`!</span><span class="sxs-lookup"><span data-stu-id="fa075-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="fa075-121">Sonsuza dek listesine yeni bir öğe ekler `a''`.</span><span class="sxs-lookup"><span data-stu-id="fa075-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="fa075-122">Nasıl, bu gerçek dünyada ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="fa075-122">How would you solve this in the real world?</span></span> <span data-ttu-id="fa075-123">İyi özgün bağlantılı listesinin bir kopyasını alın ve tamamen yeni bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa075-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="fa075-124">Veya ilk öğeyi bulabileceğiniz tamamen kesinlik temelli kod yazıyorsanız yeni öğe ekleme ve eklediğiniz öğenin ilerledikten iki kez bağlantılı listesinde ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="fa075-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="fa075-125">Yineleme sırasında ekleme</span><span class="sxs-lookup"><span data-stu-id="fa075-125">Adding While Iterating</span></span>  
 <span data-ttu-id="fa075-126">Örneğin, yinelenen bir öğe oluşturmak istediğiniz bir ağacında her bir öğe için kod yazmak istediğiniz varsayalım:</span><span class="sxs-lookup"><span data-stu-id="fa075-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="fa075-127">Bu kod bir sonsuz döngüye giriyor.</span><span class="sxs-lookup"><span data-stu-id="fa075-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="fa075-128">`foreach` Deyimi yinelenir aracılığıyla `Elements()` yeni öğeleri eklemek, eksen `doc` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fa075-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="fa075-129">Ayrıca yeni eklediğiniz öğeleri boyunca yineleme yukarı sona erer.</span><span class="sxs-lookup"><span data-stu-id="fa075-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="fa075-130">Ve bir döngünün her yinelemesinden ile yeni nesneleri ayırdığından, sonunda tüm kullanılabilir bellek tüketir.</span><span class="sxs-lookup"><span data-stu-id="fa075-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="fa075-131">Bellek kullanarak koleksiyon çekerek bu sorunu düzeltebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> aşağıdaki gibi standart sorgu işleci:</span><span class="sxs-lookup"><span data-stu-id="fa075-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="fa075-132">Artık kod çalışır.</span><span class="sxs-lookup"><span data-stu-id="fa075-132">Now the code works.</span></span> <span data-ttu-id="fa075-133">Sonuçta elde edilen XML ağacı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fa075-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="fa075-134">Yineleme sırasında siliniyor</span><span class="sxs-lookup"><span data-stu-id="fa075-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="fa075-135">Belirli bir düzeyde tüm düğümleri silmek istiyorsanız, aşağıdaki gibi bir kod yazmak için fikri size cazip olabilir:</span><span class="sxs-lookup"><span data-stu-id="fa075-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="fa075-136">Ancak, bunu istediğiniz yapmaz.</span><span class="sxs-lookup"><span data-stu-id="fa075-136">However, this does not do what you want.</span></span> <span data-ttu-id="fa075-137">Bu durumda, ilk öğe, A kaldırdıktan sonra kök dizininde bulunan XML ağacı kaldırılır ve sonraki öğeye yineleme yapmak öğeleri yöntemi kodunda bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="fa075-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="fa075-138">Yukarıdaki kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fa075-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="fa075-139">Çözümü yeniden çağırmaktır <xref:System.Linq.Enumerable.ToList%2A> koleksiyonun şu şekilde gerçekleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="fa075-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="fa075-140">Bu, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fa075-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="fa075-141">Alternatif olarak, yineleme tamamen çağırarak ortadan kaldırabileceğiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> üst öğesindeki:</span><span class="sxs-lookup"><span data-stu-id="fa075-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="fa075-142">Neden LINQ otomatik olarak bu işleyemiyor?</span><span class="sxs-lookup"><span data-stu-id="fa075-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="fa075-143">Her zaman her şeyi belleğe geç değerlendirme yapmak yerine getirmek için bir yaklaşım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa075-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="fa075-144">Ancak, performans ve bellek kullanım açısından çok pahalı olacaktı.</span><span class="sxs-lookup"><span data-stu-id="fa075-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="fa075-145">Aslında, bu yaklaşımı benimsemeye LINQ ve (LINQ to XML) olsaydı, gerçek dünyadaki koşullarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fa075-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="fa075-146">Başka bir olası bir yaklaşım işlem söz dizimi LINQ çeşit yerleştirin ve kodu analiz edin ve herhangi belirli bir koleksiyon gerçekleştirilmesi gerekli olmadığını belirlemek için derleyici denemesi sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa075-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="fa075-147">Ancak, yan etkisi olmadığı tüm kodu belirlenmeye çalışılırken son derece karmaşık olur.</span><span class="sxs-lookup"><span data-stu-id="fa075-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="fa075-148">Aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fa075-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="fa075-149">Analiz kodların TestSomeCondition ve DoMyProjection yöntemleri ve herhangi bir kod yan etkilere sahip olduğu belirlemek için bu yöntemi çağıran tüm yöntemleri analiz etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa075-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="fa075-150">Ancak, yan etkileri olan herhangi bir kod için Kod Analizi yalnızca aranamadı.</span><span class="sxs-lookup"><span data-stu-id="fa075-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="fa075-151">Alt öğeleri üzerinde yan etkileri olan kod için seçilecek gerekir `root` böyle bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fa075-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="fa075-152">Bu tür bir analiz yapmak LINQ to XML denemez.</span><span class="sxs-lookup"><span data-stu-id="fa075-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="fa075-153">Bu, bu sorunları önlemek için size bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa075-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="fa075-154">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="fa075-154">Guidance</span></span>  
 <span data-ttu-id="fa075-155">İlk olarak, bildirim temelli ve kesinlik temelli kod karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="fa075-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="fa075-156">Tam olarak koleksiyonlarınız semantiği ve sorunların bu kategorileri engelleyen akıllı kod yazma, XML ağacı değiştirme yöntemleri semantiği bilmeniz bile kodunuzun diğer geliştiriciler tarafından gelecekte saklanması gerekir , ve bunlar üzerinde sorunları olabildiğince açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fa075-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="fa075-157">Bildirim temelli ve buyurgan stilleri kodlama karıştırmak, kodunuzu daha kırılır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa075-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="fa075-158">Bir koleksiyon gerçekleştiren ve böylece bu sorunlardan kaçınılması kod yazma, bakım programcılar sorunu anlamanız, açıklamalar, kodunuzdaki uygun şekilde ile unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa075-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="fa075-159">İkinci olarak, performans ve diğer önemli noktalar izin verirseniz, yalnızca bildirim temelli bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa075-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="fa075-160">Var olan XML ağacınızı değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="fa075-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="fa075-161">Yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa075-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa075-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa075-162">See also</span></span>

- [<span data-ttu-id="fa075-163">Gelişmiş LINQ to XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="fa075-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

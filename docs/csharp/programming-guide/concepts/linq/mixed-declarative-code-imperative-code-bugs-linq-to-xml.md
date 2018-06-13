---
title: Bildirim temelli kod kesinliği kod hataları (LINQ-XML) karma (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: efc58aac69c53cda724e5fe348560a99311e8d4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337697"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="19dea-102">Bildirim temelli kod/kesinliği kod hataları (LINQ-XML) karma (C#)</span><span class="sxs-lookup"><span data-stu-id="19dea-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="19dea-103"> bir XML ağacı doğrudan değiştirmenize izin çeşitli yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="19dea-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="19dea-104">Öğeler ekleme, öğeleri silin, bir öğenin içeriğini değiştirme, öznitelikler eklemek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="19dea-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="19dea-105">Bu programlama arabirimi açıklanan [XML ağaçlarını değiştirme (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="19dea-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="19dea-106">Eksenleri, biri aracılığıyla gibi yineleme varsa <xref:System.Xml.Linq.XContainer.Elements%2A>ve eksen yineleme olarak XML ağaç değiştiriyorsunuz, bazı garip hatalarla düşebilir.</span><span class="sxs-lookup"><span data-stu-id="19dea-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="19dea-107">Bu sorun, bazen "Cadılar sorunun" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="19dea-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="19dea-108">Sorun tanımı</span><span class="sxs-lookup"><span data-stu-id="19dea-108">Definition of the Problem</span></span>  
 <span data-ttu-id="19dea-109">Bir toplulukta tekrarlanan LINQ kullanarak biraz kod yazarken, bildirim temelli stilde kodu yazıyor.</span><span class="sxs-lookup"><span data-stu-id="19dea-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="19dea-110">Açıklayan benzer daha fazla *ne* istediğiniz, bunun yerine, *nasıl* onu bitti almak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="19dea-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="19dea-111">1) ilk öğesi alır kod yazın, sonra da bu kesinlik temelli kodu olacaktır 2) testleri belli bir koşul için 3) değiştirdiği ve 4) yerleştirir listesine yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="19dea-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="19dea-112">Bilgisayar söylemiş olursunuz *nasıl* yapılmasını istediğinizi yapmak için.</span><span class="sxs-lookup"><span data-stu-id="19dea-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="19dea-113">Kod aynı işlemde bu stiller karıştırma ne sorunları müşteri adayları olur.</span><span class="sxs-lookup"><span data-stu-id="19dea-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="19dea-114">Aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="19dea-114">Consider the following:</span></span>  
  
 <span data-ttu-id="19dea-115">Üç öğeleri ile bağlantılı bir liste içinde olduğunu varsayalım (a, b ve c):</span><span class="sxs-lookup"><span data-stu-id="19dea-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="19dea-116">Şimdi, bağlantılı liste taşımak üç yeni öğeler eklemek istediğinizi varsayalım (bir ', b' ve c').</span><span class="sxs-lookup"><span data-stu-id="19dea-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="19dea-117">Şuna için sonuçta elde edilen bağlantılı liste istediğiniz:</span><span class="sxs-lookup"><span data-stu-id="19dea-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="19dea-118">Bu nedenle listesi kullanılarak ve her öğe için tekrarlanan kod yazma yeni öğeyi sağ sonra ekler.</span><span class="sxs-lookup"><span data-stu-id="19dea-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="19dea-119">Kodunuzu ilk göreceği gerçekleşir `a` öğesi ve INSERT `a'` sonraki.</span><span class="sxs-lookup"><span data-stu-id="19dea-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="19dea-120">Şimdi, kodunuzu artık listesindeki bir sonraki düğüme taşır `a'`!</span><span class="sxs-lookup"><span data-stu-id="19dea-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="19dea-121">Sonsuza dek listesine yeni bir öğe ekler `a''`.</span><span class="sxs-lookup"><span data-stu-id="19dea-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="19dea-122">Nasıl, bu gerçek dünyada ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="19dea-122">How would you solve this in the real world?</span></span> <span data-ttu-id="19dea-123">İyi, özgün bağlantılı listesinin bir kopyasını alın ve tamamen yeni bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19dea-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="19dea-124">Veya ilk öğe bulabileceğiniz tamamen kesinlik temelli kod yazıyorsanız, yeni öğe eklemek ve yeni eklediğiniz öğenin üzerine ilerledikten iki kez bağlantılı listesinde ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="19dea-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="19dea-125">Yineleme sırasında ekleme</span><span class="sxs-lookup"><span data-stu-id="19dea-125">Adding While Iterating</span></span>  
 <span data-ttu-id="19dea-126">Örneğin, yinelenen bir öğe oluşturmak istediğiniz bir ağacında her öğe için biraz kod yazmaya istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="19dea-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="19dea-127">Bu kod sonsuz döngüye girer.</span><span class="sxs-lookup"><span data-stu-id="19dea-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="19dea-128">`foreach` Deyimi tekrarlanan aracılığıyla `Elements()` eksen için yeni öğe eklemek, `doc` öğesi.</span><span class="sxs-lookup"><span data-stu-id="19dea-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="19dea-129">Ayrıca aracılığıyla yeni eklenen öğelerin yineleme yukarı sona erer.</span><span class="sxs-lookup"><span data-stu-id="19dea-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="19dea-130">Ve yeni nesneler her döngü ile ayırdığından, sonunda tüm kullanılabilir bellek tüketir.</span><span class="sxs-lookup"><span data-stu-id="19dea-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="19dea-131">Bellek kullanarak koleksiyon çekerek bu sorunu düzeltebilirsiniz <xref:System.Linq.Enumerable.ToList%2A> aşağıdaki gibi standart sorgu işleci:</span><span class="sxs-lookup"><span data-stu-id="19dea-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="19dea-132">Şimdi kodu çalışır.</span><span class="sxs-lookup"><span data-stu-id="19dea-132">Now the code works.</span></span> <span data-ttu-id="19dea-133">Sonuçta elde edilen XML ağaç aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="19dea-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="19dea-134">Yineleme sırasında silme</span><span class="sxs-lookup"><span data-stu-id="19dea-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="19dea-135">Belirli bir düzeyde tüm düğümleri silmek istiyorsanız, aşağıdaki gibi bir kod yazmak için isteği olabilir:</span><span class="sxs-lookup"><span data-stu-id="19dea-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="19dea-136">Ancak, bunu istediğinizi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="19dea-136">However, this does not do what you want.</span></span> <span data-ttu-id="19dea-137">Bu durumda, ilk öğe, A kaldırdıktan sonra kökünde bulunan XML ağacından kaldırıldı ve yineleme yaptığını öğeleri yöntemi kodda sonraki öğesi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="19dea-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="19dea-138">Önceki kod şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="19dea-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="19dea-139">Çözümü yeniden çağırmaktır <xref:System.Linq.Enumerable.ToList%2A> koleksiyonu gibi gerçekleştirmeye için:</span><span class="sxs-lookup"><span data-stu-id="19dea-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="19dea-140">Bu şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="19dea-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="19dea-141">Alternatif olarak, yineleme tamamen çağırarak ortadan kaldırabileceğiniz <xref:System.Xml.Linq.XElement.RemoveAll%2A> üst öğede:</span><span class="sxs-lookup"><span data-stu-id="19dea-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="19dea-142">Neden LINQ otomatik olarak bu işleyemiyor?</span><span class="sxs-lookup"><span data-stu-id="19dea-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="19dea-143">Bir yaklaşım, her zaman her şeyi belleğe geç değerlendirme yapmak yerine getirmek için olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19dea-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="19dea-144">Ancak, performans ve bellek kullanımı açısından çok pahalı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19dea-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="19dea-145">Aslında, bu yaklaşımı benimsemeye LINQ ve (LINQ-XML) olsaydı, gerçek durumlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="19dea-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="19dea-146">Başka bir olası yaklaşım işlem sözdizimi LINQ çeşit koyun ve kod çözümlemek ve belirli bir koleksiyon gerçekleştirilmesi gerekli olmadığını belirlemek için derleyici girişimi sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19dea-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="19dea-147">Ancak, yan etkileri olan tüm kodu belirlenmeye çalışılırken son derece karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="19dea-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="19dea-148">Aşağıdaki kod göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="19dea-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="19dea-149">Bu tür Analiz kodu TestSomeCondition ve DoMyProjection yöntemleri ve herhangi bir kod yan etkileri sahip belirlemek için bu yöntem çağrılır tüm yöntemleri çözümlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="19dea-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="19dea-150">Ancak yan etkileri olan herhangi bir kod için Kod Analizine yalnızca aranamadı.</span><span class="sxs-lookup"><span data-stu-id="19dea-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="19dea-151">İçin alt öğelerde yan etkileri olan kodu seçmeniz gerekir `root` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="19dea-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="19dea-152">LINQ-XML gibi bir analiz yapma denemez.</span><span class="sxs-lookup"><span data-stu-id="19dea-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="19dea-153">Bu sorunları önlemek için size bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="19dea-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="19dea-154">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="19dea-154">Guidance</span></span>  
 <span data-ttu-id="19dea-155">İlk olarak, bildirim temelli ve kesinlik temelli kodu karışık kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="19dea-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="19dea-156">Tam olarak koleksiyonlarınızı semantiği ve bu kategoriler sorunları önler akıllı biraz kod yazarsanız XML ağaç değiştirme yöntemleri semantiği bildiğiniz olsa bile, kodunuzu diğer geliştiriciler tarafından gelecekte saklanması gerekir , ve bunların sorunlarını olabildiğince açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="19dea-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="19dea-157">Bildirim temelli ve kesinlik temelli stilleri kodlama karıştırmak, kodunuzu daha kırılır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19dea-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="19dea-158">Bir koleksiyon gerçeğe ve böylece bu sorunlardan kaçınılması kodu yazarsanız, böylece bakım programcıları sorunu anlayabileceği, kodunuzda uygun şekilde yorumlarla unutmayın.</span><span class="sxs-lookup"><span data-stu-id="19dea-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="19dea-159">İkinci olarak, performans ve diğer konular için izin verirseniz, yalnızca bildirim temelli kodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="19dea-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="19dea-160">Varolan bir XML ağacında değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="19dea-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="19dea-161">Yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19dea-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19dea-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19dea-162">See Also</span></span>  
 [<span data-ttu-id="19dea-163">Gelişmiş LINQ-XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="19dea-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

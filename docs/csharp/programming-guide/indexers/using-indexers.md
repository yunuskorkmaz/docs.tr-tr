---
title: "Dizin Oluşturucular Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 17bbfabe8a53fc51e81434d0a2bd9fb2b29c4695
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="4b8c6-102">Dizin Oluşturucular Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4b8c6-102">Using Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="4b8c6-103">Dizin oluşturucular oluşturmanıza olanak sağlayan bir söz dizimi kullanışlı olan bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapısı](../../../csharp/language-reference/keywords/struct.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) istemci uygulamaları, bir dizi olarak erişebilir.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="4b8c6-104">Dizin oluşturucular en sık birincil amacı olan bir iç toplama veya dizi kapsülleyen türlerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="4b8c6-105">Örneğin, 24 saatlik bir dönemde 10 farklı saatlerinde kayıtlı olan Farenheit sıcaklık temsil eden TempRecord adlı bir sınıf olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-105">For example, suppose you have a class named TempRecord that represents the temperature in Farenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="4b8c6-106">"Etme temsil etmek için temps" float türünde adlı bir dizi sınıf içerir ve bir <xref:System.DateTime> etme kaydedilen tarih temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-106">The class contains an array named "temps" of type float to represent the temperatures, and a <xref:System.DateTime> that represents the date the temperatures were recorded.</span></span> <span data-ttu-id="4b8c6-107">Bu sınıf bir dizin oluşturucu uygulayarak istemcileri TempRecord örneğinde etme erişebilir `float temp = tr[4]` yerine olarak `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-107">By implementing an indexer in this class, clients can access the temperatures in a TempRecord instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="4b8c6-108">Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için söz dizimi basitleştirir; Ayrıca sınıf ve amacı anlamak diğer geliştiriciler için daha sezgisel kılar.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
 <span data-ttu-id="4b8c6-109">Bir dizin oluşturucu bir sınıf veya yapı bildirmek için kullanın [bu](../../../csharp/language-reference/keywords/this.md) Bu örnekte olduğu gibi anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="4b8c6-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as in this example:</span></span>  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b8c6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b8c6-110">Remarks</span></span>  
 <span data-ttu-id="4b8c6-111">Bir dizin oluşturucu türünü ve parametreleri türünü en az dizinleyici olarak erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="4b8c6-112">Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4b8c6-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4b8c6-113">Dizin oluşturucular bir arabirim ile kullanma hakkında daha fazla bilgi için bkz: [arabirim Dizinleyicileri](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4b8c6-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="4b8c6-114">Bir dizin oluşturucu imza sayısı ve türleri resmi parametrelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="4b8c6-115">Dizin Oluşturucu türü veya biçimsel parametresi adları içermez.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-115">It does not include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="4b8c6-116">Aynı sınıf içinde birden çok dizin oluşturucu bildirirseniz farklı imzalar olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="4b8c6-117">Bir dizin oluşturucu değeri bir değişken olarak sınıflandırılmış değil; Bu nedenle, bir dizin oluşturucu değeri olarak geçiremezsiniz bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="4b8c6-118">Dizin Oluşturucu, diğer diller kullanabileceği bir ad ile sağlamak için kullanın bir `name` öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-118">To provide the indexer with a name that other languages can use, use a `name` attribute in the declaration.</span></span> <span data-ttu-id="4b8c6-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4b8c6-119">For example:</span></span>  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 <span data-ttu-id="4b8c6-120">Bu dizin oluşturucu ada sahip olacaktır `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-120">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="4b8c6-121">Ad özniteliği sağlama değil olun `Item` varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-121">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="4b8c6-122">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="4b8c6-122">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="4b8c6-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b8c6-123">Description</span></span>  
 <span data-ttu-id="4b8c6-124">Aşağıdaki örnek, bir özel dizi alan bildirmek gösterilmiştir `temps`ve bir dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-124">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="4b8c6-125">Dizin oluşturucu örneği doğrudan erişim sağlayan `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-125">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="4b8c6-126">Dizin Oluşturucu kullanarak alternatif bir dizi olarak bildirmektir bir [ortak](../../../csharp/language-reference/keywords/public.md) üye ve bu grubun üyeleri erişim `tempRecord.temps[i]`, doğrudan.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-126">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="4b8c6-127">Bir oluşturucunun erişim, örneğin, içinde değerlendirmesinde dikkat bir `Console.Write` deyimi, [almak](../../../csharp/language-reference/keywords/get.md) erişimci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-127">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="4b8c6-128">Bu nedenle, yoksa `get` erişimci yoksa, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-128">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4b8c6-129">Kod</span><span class="sxs-lookup"><span data-stu-id="4b8c6-129">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="4b8c6-130">Diğer değerleri kullanarak dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b8c6-130">Indexing Using Other Values</span></span>  
 <span data-ttu-id="4b8c6-131">C# dizin türü tamsayı sınırlamaz.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-131">C# does not limit the index type to integer.</span></span> <span data-ttu-id="4b8c6-132">Örneğin, bir dizeyi bir dizin oluşturucu ile kullanmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-132">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="4b8c6-133">Böyle bir dizin oluşturucu, koleksiyondaki dizesi için arama ve uygun değer döndürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-133">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="4b8c6-134">Dize ve tamsayı sürümleri erişimciler aşırı olarak birlikte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-134">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="4b8c6-135">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="4b8c6-135">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="4b8c6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b8c6-136">Description</span></span>  
 <span data-ttu-id="4b8c6-137">Bu örnekte, bir sınıf haftanın günlerini depolar bildirildi.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-137">In this example, a class is declared that stores the days of the week.</span></span> <span data-ttu-id="4b8c6-138">A `get` erişimci bildirilen bir gün adı bir dize alır ve karşılık gelen tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-138">A `get` accessor is declared that takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="4b8c6-139">Örneğin, Pazar 0 döndürür, Pazartesi 1 dönmek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-139">For example, Sunday will return 0, Monday will return 1, and so on.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4b8c6-140">Kod</span><span class="sxs-lookup"><span data-stu-id="4b8c6-140">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4b8c6-141">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4b8c6-141">Robust Programming</span></span>  
 <span data-ttu-id="4b8c6-142">İçinde güvenlik ve dizin oluşturucular güvenilirliğini geliştirilebilir başlıca iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="4b8c6-142">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
-   <span data-ttu-id="4b8c6-143">Hata işleme stratejisi ' geçersiz dizin değeri geçirme istemci kodu olasılığını işlemek için bir tür eklemenizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-143">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="4b8c6-144">Bu konunun önceki kısımlarında ilk örnekte TempRecord sınıfı için dizin oluşturucu geçirmeden önce giriş doğrulamak istemci kodu sağlayan bir Length özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-144">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="4b8c6-145">Hata işleme kodunu dizinleyici içinde de yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-145">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="4b8c6-146">İçinde bir dizin oluşturucu erişimci throw tüm özel durumlar için kullanıcıların belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-146">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
-   <span data-ttu-id="4b8c6-147">Erişilebilirliğini ayarlamak `get` ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimciler şüphelenilebilir olabildiğince kısıtlayıcı olun.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-147">Set the accessibility of the `get` and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="4b8c6-148">Bu önemlidir `set` belirli erişimci.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-148">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="4b8c6-149">Daha fazla bilgi için bkz: [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="4b8c6-149">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8c6-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b8c6-150">See Also</span></span>  
 [<span data-ttu-id="4b8c6-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4b8c6-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4b8c6-152">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="4b8c6-152">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="4b8c6-153">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4b8c6-153">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

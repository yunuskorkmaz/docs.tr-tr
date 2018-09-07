---
title: Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: ded8840231c4860d538eeb8c24d1472c60426087
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084837"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="f1ce9-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f1ce9-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="f1ce9-103">Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="f1ce9-104">CLR bir değer türünü kutu, değeri içinde bir System.Object nesnesiyle sarar ve Yönetilen öbekte depolar.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="f1ce9-105">Kutudan çıkarma, değer türünü nesneden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="f1ce9-106">Örtük kutulama; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="f1ce9-107">Kutulama ve kutudan çıkarma kavramı, C# birleştirilmiş görünümünü herhangi bir türde bir değer bir nesne işlenebilir tür sistemi vurgular.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="f1ce9-108">Aşağıdaki örnekte, tam sayı değişkeni `i` olduğu *Kutulu* ve nesneye atanmış `o`.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 <span data-ttu-id="f1ce9-109">Nesne `o` ardından kullanılabilir kutudan çıkarılır ve tamsayı değişkenine atanır `i`:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 <span data-ttu-id="f1ce9-110">Aşağıdaki örnekler, nasıl kutulama C# dilinde kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a><span data-ttu-id="f1ce9-111">Performans</span><span class="sxs-lookup"><span data-stu-id="f1ce9-111">Performance</span></span>  
 <span data-ttu-id="f1ce9-112">Basit atamalara ilişkin, kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="f1ce9-113">Bir değer türü kutulandığında, yeni bir nesne ayrılan ve oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="f1ce9-114">Daha düşük bir düzeyde olmak kaydıyla kutudan çıkarmak için gereken dönüştürme de hesaplama açısından pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="f1ce9-115">Daha fazla bilgi için [performans](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="f1ce9-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="f1ce9-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="f1ce9-116">Boxing</span></span>  
 <span data-ttu-id="f1ce9-117">Kutulama, değer türleri içinde atık olarak toplanmış yığınla depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="f1ce9-118">Örtük kutulama olduğu bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="f1ce9-119">Bir değer türü kutulama, yığındaki bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="f1ce9-120">Aşağıdaki değer türündeki değişken bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 <span data-ttu-id="f1ce9-121">Aşağıdaki deyim örtük olarak kutulama işlemini değişkeni geçerlidir `i`:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 <span data-ttu-id="f1ce9-122">Bu ifade sonucu, bir nesne başvurusu oluşturur `o`, stack türünde bir değer başvuran `int`, yığında.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="f1ce9-123">Bu değer değişkenine atanan değer türü değerinin bir kopyasıdır `i`.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="f1ce9-124">İki değişken arasındaki farkı `i` ve `o`, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="f1ce9-125">![BoxingConversion grafiği](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="f1ce9-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="f1ce9-126">Paketleme dönüştürmesi</span><span class="sxs-lookup"><span data-stu-id="f1ce9-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="f1ce9-127">Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a><span data-ttu-id="f1ce9-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1ce9-128">Description</span></span>  
 <span data-ttu-id="f1ce9-129">Bu örnek, bir tam sayı değişkeni dönüştürür `i` nesneye `o` kutulama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="f1ce9-130">Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="f1ce9-131">Örnek, baştaki değer türünün ve kutulanmış nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depoluyor olabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ce9-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1ce9-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a><span data-ttu-id="f1ce9-133">Kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="f1ce9-133">Unboxing</span></span>  
 <span data-ttu-id="f1ce9-134">Kutudan çıkarma bir dönüştürmedir türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya bir arabirim türünden arabirimi uygulayan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="f1ce9-135">Bir kutudan çıkarma işlemi şunlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="f1ce9-136">Verilen değer türünün kutulanmış bir değer olduğundan emin olmak için nesne örneğini denetleme.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="f1ce9-137">Değerin örnekten değer türü değişkenine kopyalanması.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="f1ce9-138">Aşağıdaki deyimleri, kutulama ve kutudan çıkarma işlemlerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 <span data-ttu-id="f1ce9-139">Aşağıdaki şekil önceki deyimlerin sonucunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="f1ce9-140">![Kutudan çıkarma dönüştürme grafik](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="f1ce9-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="f1ce9-141">Kutudan çıkarma dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f1ce9-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="f1ce9-142">Çalışma zamanında başarılı olması için değer türlerinin kaydıyla kutudan çıkarmak için kutulanarak öğe kutulama, değer türünün bir örneği tarafından daha önce oluşturulmuş bir nesneye bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="f1ce9-143">Açmaya `null` neden olan bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="f1ce9-144">Türüne neden uyumsuz bir değere bir başvuru açmaya bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ce9-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1ce9-145">Example</span></span>  
 <span data-ttu-id="f1ce9-146">Aşağıdaki örnek, geçersiz bir kutulama bir kullanım durumu ve ortaya çıkan gösterir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="f1ce9-147">Kullanarak `try` ve `catch`, hata oluştuğunda bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 <span data-ttu-id="f1ce9-148">Bu programın çıktısı şudur:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="f1ce9-149">Deyimi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-149">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="f1ce9-150">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-150">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="f1ce9-151">dönüştürme yapılır ve şu çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="f1ce9-152">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f1ce9-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="f1ce9-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f1ce9-153">Related Sections</span></span>  
 <span data-ttu-id="f1ce9-154">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="f1ce9-154">For more information:</span></span>  
  
-   [<span data-ttu-id="f1ce9-155">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="f1ce9-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="f1ce9-156">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="f1ce9-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1ce9-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ce9-157">See Also</span></span>

- [<span data-ttu-id="f1ce9-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1ce9-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

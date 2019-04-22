---
title: Kutulama ve kutudan çıkarma - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: da4aabbd0529ee239dacd2dff7c7825d41110b44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835173"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="243c3-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="243c3-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="243c3-103">Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="243c3-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="243c3-104">CLR bir değer türünü kutu, değeri içinde bir System.Object nesnesiyle sarar ve Yönetilen öbekte depolar.</span><span class="sxs-lookup"><span data-stu-id="243c3-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="243c3-105">Kutudan çıkarma, değer türünü nesneden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="243c3-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="243c3-106">Örtük kutulama; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="243c3-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="243c3-107">Kutulama ve kutudan çıkarma kavramı, C# birleştirilmiş görünümünü herhangi bir türde bir değer bir nesne işlenebilir tür sistemi vurgular.</span><span class="sxs-lookup"><span data-stu-id="243c3-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="243c3-108">Aşağıdaki örnekte, tam sayı değişkeni `i` olduğu *Kutulu* ve nesneye atanmış `o`.</span><span class="sxs-lookup"><span data-stu-id="243c3-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="243c3-109">Nesne `o` ardından kullanılabilir kutudan çıkarılır ve tamsayı değişkenine atanır `i`:</span><span class="sxs-lookup"><span data-stu-id="243c3-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="243c3-110">Aşağıdaki örnekler, nasıl kutulama C# dilinde kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="243c3-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="243c3-111">Performans</span><span class="sxs-lookup"><span data-stu-id="243c3-111">Performance</span></span>  
 <span data-ttu-id="243c3-112">Basit atamalara ilişkin, kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="243c3-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="243c3-113">Bir değer türü kutulandığında, yeni bir nesne ayrılan ve oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="243c3-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="243c3-114">Daha düşük bir düzeyde olmak kaydıyla kutudan çıkarmak için gereken dönüştürme de hesaplama açısından pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="243c3-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="243c3-115">Daha fazla bilgi için [performans](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="243c3-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="243c3-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="243c3-116">Boxing</span></span>  
 <span data-ttu-id="243c3-117">Kutulama, değer türleri içinde atık olarak toplanmış yığınla depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="243c3-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="243c3-118">Örtük kutulama olduğu bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="243c3-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="243c3-119">Bir değer türü kutulama, yığındaki bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="243c3-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="243c3-120">Aşağıdaki değer türündeki değişken bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="243c3-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="243c3-121">Aşağıdaki deyim örtük olarak kutulama işlemini değişkeni geçerlidir `i`:</span><span class="sxs-lookup"><span data-stu-id="243c3-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="243c3-122">Bu ifade sonucu, bir nesne başvurusu oluşturur `o`, stack türünde bir değer başvuran `int`, yığında.</span><span class="sxs-lookup"><span data-stu-id="243c3-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="243c3-123">Bu değer değişkenine atanan değer türü değerinin bir kopyasıdır `i`.</span><span class="sxs-lookup"><span data-stu-id="243c3-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="243c3-124">İki değişken arasındaki farkı `i` ve `o`, paketleme dönüştürmesi, aşağıdaki görüntüde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="243c3-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>  
  
 ![İ o arasındaki farkı gösteren grafik değişkenleri.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 <span data-ttu-id="243c3-126">Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="243c3-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="243c3-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="243c3-127">Description</span></span>  
 <span data-ttu-id="243c3-128">Bu örnek, bir tam sayı değişkeni dönüştürür `i` nesneye `o` kutulama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="243c3-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="243c3-129">Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`.</span><span class="sxs-lookup"><span data-stu-id="243c3-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="243c3-130">Örnek, baştaki değer türünün ve kutulanmış nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depoluyor olabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="243c3-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="243c3-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="243c3-131">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="243c3-132">Kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="243c3-132">Unboxing</span></span>  
 <span data-ttu-id="243c3-133">Kutudan çıkarma bir dönüştürmedir türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya bir arabirim türünden arabirimi uygulayan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="243c3-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="243c3-134">Bir kutudan çıkarma işlemi şunlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="243c3-134">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="243c3-135">Verilen değer türünün kutulanmış bir değer olduğundan emin olmak için nesne örneğini denetleme.</span><span class="sxs-lookup"><span data-stu-id="243c3-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="243c3-136">Değerin örnekten değer türü değişkenine kopyalanması.</span><span class="sxs-lookup"><span data-stu-id="243c3-136">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="243c3-137">Aşağıdaki deyimleri, kutulama ve kutudan çıkarma işlemlerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="243c3-137">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="243c3-138">Aşağıdaki şekil önceki deyimlerin sonucunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="243c3-138">The following figure demonstrates the result of the previous statements:</span></span> 
  
 ![Bir paketi açma dönüştürmesi gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 <span data-ttu-id="243c3-140">Çalışma zamanında başarılı olması için değer türlerinin kaydıyla kutudan çıkarmak için kutulanarak öğe kutulama, değer türünün bir örneği tarafından daha önce oluşturulmuş bir nesneye bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="243c3-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="243c3-141">Açmaya `null` neden olan bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="243c3-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="243c3-142">Türüne neden uyumsuz bir değere bir başvuru açmaya bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="243c3-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="243c3-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="243c3-143">Example</span></span>  
 <span data-ttu-id="243c3-144">Aşağıdaki örnek, geçersiz bir kutulama bir kullanım durumu ve ortaya çıkan gösterir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="243c3-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="243c3-145">Kullanarak `try` ve `catch`, hata oluştuğunda bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="243c3-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="243c3-146">Bu programın çıktısı şudur:</span><span class="sxs-lookup"><span data-stu-id="243c3-146">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="243c3-147">Deyimi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="243c3-147">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="243c3-148">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="243c3-148">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="243c3-149">dönüştürme yapılır ve şu çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="243c3-149">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="243c3-150">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="243c3-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="243c3-151">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="243c3-151">Related Sections</span></span>  
 <span data-ttu-id="243c3-152">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="243c3-152">For more information:</span></span>  
  
-   [<span data-ttu-id="243c3-153">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="243c3-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="243c3-154">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="243c3-154">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="243c3-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="243c3-155">See also</span></span>

- [<span data-ttu-id="243c3-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="243c3-156">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

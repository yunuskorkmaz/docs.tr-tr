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
ms.openlocfilehash: 8340d05b18c4fb19e9ba8f8ecffa5657b7febd79
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201761"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="6a37f-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6a37f-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="6a37f-103">Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="6a37f-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="6a37f-104">CLR bir değer türünü kutu, değeri içinde bir System.Object nesnesiyle sarar ve Yönetilen öbekte depolar.</span><span class="sxs-lookup"><span data-stu-id="6a37f-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="6a37f-105">Kutudan çıkarma, değer türünü nesneden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6a37f-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="6a37f-106">Örtük kutulama; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="6a37f-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="6a37f-107">Kutulama ve kutudan çıkarma kavramı, C# birleştirilmiş görünümünü herhangi bir türde bir değer bir nesne işlenebilir tür sistemi vurgular.</span><span class="sxs-lookup"><span data-stu-id="6a37f-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="6a37f-108">Aşağıdaki örnekte, tam sayı değişkeni `i` olduğu *Kutulu* ve nesneye atanmış `o`.</span><span class="sxs-lookup"><span data-stu-id="6a37f-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="6a37f-109">Nesne `o` ardından kullanılabilir kutudan çıkarılır ve tamsayı değişkenine atanır `i`:</span><span class="sxs-lookup"><span data-stu-id="6a37f-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="6a37f-110">Aşağıdaki örnekler, nasıl kutulama C# dilinde kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="6a37f-111">Performans</span><span class="sxs-lookup"><span data-stu-id="6a37f-111">Performance</span></span>  
 <span data-ttu-id="6a37f-112">Basit atamalara ilişkin, kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="6a37f-113">Bir değer türü kutulandığında, yeni bir nesne ayrılan ve oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="6a37f-114">Daha düşük bir düzeyde olmak kaydıyla kutudan çıkarmak için gereken dönüştürme de hesaplama açısından pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a37f-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="6a37f-115">Daha fazla bilgi için [performans](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="6a37f-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="6a37f-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="6a37f-116">Boxing</span></span>  
 <span data-ttu-id="6a37f-117">Kutulama, değer türleri içinde atık olarak toplanmış yığınla depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a37f-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="6a37f-118">Örtük kutulama olduğu bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne.</span><span class="sxs-lookup"><span data-stu-id="6a37f-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="6a37f-119">Bir değer türü kutulama, yığındaki bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6a37f-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="6a37f-120">Aşağıdaki değer türündeki değişken bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6a37f-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="6a37f-121">Aşağıdaki deyim örtük olarak kutulama işlemini değişkeni geçerlidir `i`:</span><span class="sxs-lookup"><span data-stu-id="6a37f-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="6a37f-122">Bu ifade sonucu, bir nesne başvurusu oluşturur `o`, stack türünde bir değer başvuran `int`, yığında.</span><span class="sxs-lookup"><span data-stu-id="6a37f-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="6a37f-123">Bu değer değişkenine atanan değer türü değerinin bir kopyasıdır `i`.</span><span class="sxs-lookup"><span data-stu-id="6a37f-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="6a37f-124">İki değişken arasındaki farkı `i` ve `o`, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="6a37f-125">![BoxingConversion grafiği](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="6a37f-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="6a37f-126">Paketleme dönüştürmesi</span><span class="sxs-lookup"><span data-stu-id="6a37f-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="6a37f-127">Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="6a37f-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="6a37f-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a37f-128">Description</span></span>  
 <span data-ttu-id="6a37f-129">Bu örnek, bir tam sayı değişkeni dönüştürür `i` nesneye `o` kutulama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6a37f-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="6a37f-130">Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`.</span><span class="sxs-lookup"><span data-stu-id="6a37f-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="6a37f-131">Örnek, baştaki değer türünün ve kutulanmış nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depoluyor olabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a37f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a37f-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="6a37f-133">Kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="6a37f-133">Unboxing</span></span>  
 <span data-ttu-id="6a37f-134">Kutudan çıkarma bir dönüştürmedir türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya bir arabirim türünden arabirimi uygulayan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="6a37f-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="6a37f-135">Bir kutudan çıkarma işlemi şunlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="6a37f-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="6a37f-136">Verilen değer türünün kutulanmış bir değer olduğundan emin olmak için nesne örneğini denetleme.</span><span class="sxs-lookup"><span data-stu-id="6a37f-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="6a37f-137">Değerin örnekten değer türü değişkenine kopyalanması.</span><span class="sxs-lookup"><span data-stu-id="6a37f-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="6a37f-138">Aşağıdaki deyimleri, kutulama ve kutudan çıkarma işlemlerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6a37f-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="6a37f-139">Aşağıdaki şekil önceki deyimlerin sonucunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="6a37f-140">![Kutudan çıkarma dönüştürme grafik](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="6a37f-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="6a37f-141">Kutudan çıkarma dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6a37f-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="6a37f-142">Çalışma zamanında başarılı olması için değer türlerinin kaydıyla kutudan çıkarmak için kutulanarak öğe kutulama, değer türünün bir örneği tarafından daha önce oluşturulmuş bir nesneye bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a37f-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="6a37f-143">Açmaya `null` neden olan bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="6a37f-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="6a37f-144">Türüne neden uyumsuz bir değere bir başvuru açmaya bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6a37f-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a37f-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a37f-145">Example</span></span>  
 <span data-ttu-id="6a37f-146">Aşağıdaki örnek, geçersiz bir kutulama bir kullanım durumu ve ortaya çıkan gösterir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="6a37f-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="6a37f-147">Kullanarak `try` ve `catch`, hata oluştuğunda bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6a37f-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="6a37f-148">Bu programın çıktısı şudur:</span><span class="sxs-lookup"><span data-stu-id="6a37f-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="6a37f-149">Deyimi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="6a37f-149">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="6a37f-150">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="6a37f-150">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="6a37f-151">dönüştürme yapılır ve şu çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="6a37f-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="6a37f-152">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6a37f-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="6a37f-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6a37f-153">Related Sections</span></span>  
 <span data-ttu-id="6a37f-154">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="6a37f-154">For more information:</span></span>  
  
-   [<span data-ttu-id="6a37f-155">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="6a37f-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="6a37f-156">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="6a37f-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a37f-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a37f-157">See also</span></span>

- [<span data-ttu-id="6a37f-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6a37f-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

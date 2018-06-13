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
ms.openlocfilehash: 4cf6a81a2738d4aff94089c89fcc39e785127a82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336137"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="883d3-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="883d3-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="883d3-103">Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` veya herhangi bir arabirim türüne bu değer türü tarafından uygulanan.</span><span class="sxs-lookup"><span data-stu-id="883d3-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="883d3-104">Değer türü CLR kutuları, bir System.Object içindeki değeri sarmalar ve yönetilen yığında depolar.</span><span class="sxs-lookup"><span data-stu-id="883d3-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="883d3-105">Kutudan çıkarma değer türü nesneden ayıklar.</span><span class="sxs-lookup"><span data-stu-id="883d3-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="883d3-106">Örtük kutulama; kutudan çıkarma açık değil.</span><span class="sxs-lookup"><span data-stu-id="883d3-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="883d3-107">Kutulama ve kutudan çıkarma kavramı herhangi türde bir değer bir nesne işlenebilir türü sistem C# Birleşik görünümü vurgular.</span><span class="sxs-lookup"><span data-stu-id="883d3-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="883d3-108">Aşağıdaki örnekte, tamsayı değişken `i` olan *Kutulu* ve nesne atanan `o`.</span><span class="sxs-lookup"><span data-stu-id="883d3-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 <span data-ttu-id="883d3-109">Nesne `o` sonra kullanılabilir sarmalanmamış ve tamsayı değişkenine atanan `i`:</span><span class="sxs-lookup"><span data-stu-id="883d3-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 <span data-ttu-id="883d3-110">Aşağıdaki örnekler nasıl kutulama C# ' ta kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="883d3-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a><span data-ttu-id="883d3-111">Performans</span><span class="sxs-lookup"><span data-stu-id="883d3-111">Performance</span></span>  
 <span data-ttu-id="883d3-112">Basit atama ile ilgili olarak kutulama ve kutudan çıkarma pkı'ya pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="883d3-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="883d3-113">Değer türü Kutulu, yeni bir nesne ayrılmış ve oluşturulan gerekir.</span><span class="sxs-lookup"><span data-stu-id="883d3-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="883d3-114">Daha düşük bir dereceye kutudan çıkarma için gerekli cast de pkı'ya maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="883d3-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="883d3-115">Daha fazla bilgi için bkz: [performans](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="883d3-115">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="883d3-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="883d3-116">Boxing</span></span>  
 <span data-ttu-id="883d3-117">Kutulama değer türleri çöpünün toplanma yığınında depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="883d3-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="883d3-118">Kutulama olduğu örtük bir dönüştürme bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` veya herhangi bir arabirim türüne bu değer türü tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="883d3-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="883d3-119">Değer türü kutulama nesne örneği yığında ayırır ve değeri yeni nesnesine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="883d3-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="883d3-120">Değer türü değişkeni aşağıdaki bildirimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="883d3-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 <span data-ttu-id="883d3-121">Aşağıdaki deyim örtük olarak değişkeni paketleme işlemi uygular `i`:</span><span class="sxs-lookup"><span data-stu-id="883d3-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 <span data-ttu-id="883d3-122">Bu deyimi sonucunu bir nesne başvurusu oluşturma `o`, yığında türünde bir değer başvuran `int`, yığında.</span><span class="sxs-lookup"><span data-stu-id="883d3-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="883d3-123">Bu değer değişkenine atanan değer türü değeri kopyasıdır `i`.</span><span class="sxs-lookup"><span data-stu-id="883d3-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="883d3-124">İki değişken arasındaki farkı `i` ve `o`, aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="883d3-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="883d3-125">![BoxingConversion grafiği](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="883d3-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="883d3-126">Kutulama dönüştürme</span><span class="sxs-lookup"><span data-stu-id="883d3-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="883d3-127">Aşağıdaki örnekteki gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gereklidir:</span><span class="sxs-lookup"><span data-stu-id="883d3-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a><span data-ttu-id="883d3-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="883d3-128">Description</span></span>  
 <span data-ttu-id="883d3-129">Bu örnek bir tamsayı değişken dönüştürür `i` bir nesneye `o` kutulama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="883d3-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="883d3-130">Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`.</span><span class="sxs-lookup"><span data-stu-id="883d3-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="883d3-131">Bu örnek, özgün değer türü ve sarmalanmış nesne ayrı bir bellek konumlarını kullanın ve bu nedenle farklı değerler saklayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="883d3-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="883d3-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="883d3-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a><span data-ttu-id="883d3-133">Kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="883d3-133">Unboxing</span></span>  
 <span data-ttu-id="883d3-134">Kutudan çıkarma olan açık bir dönüştürme türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya arabirimini uygulayan bir değer türü için bir arabirim türü.</span><span class="sxs-lookup"><span data-stu-id="883d3-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="883d3-135">Kutudan çıkarma işlemi şunlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="883d3-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="883d3-136">Paketlenmiş değere verilen değer türü olduğundan emin olmak için nesne örneği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="883d3-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="883d3-137">Değer, değer türü değişkeni örneğine kopyalama.</span><span class="sxs-lookup"><span data-stu-id="883d3-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="883d3-138">Aşağıdaki deyimleri hem kutulama ve kutudan çıkarma işlemleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="883d3-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 <span data-ttu-id="883d3-139">Aşağıdaki şekilde, önceki deyimleri sonucunu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="883d3-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="883d3-140">![Kutudan çıkarma dönüşüm grafiği](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="883d3-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="883d3-141">Kutudan çıkarma dönüştürme</span><span class="sxs-lookup"><span data-stu-id="883d3-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="883d3-142">Çalışma zamanında başarılı olması için değer türlerini kutudan çıkarma için bu değer türünün bir örneği kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru sarmalanmamış öğe olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="883d3-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="883d3-143">Unbox çalışılıyor `null` neden olan bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="883d3-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="883d3-144">Uyumlu olmayan bir değer için bir başvuru unbox çalışılıyor yazın neden bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="883d3-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="883d3-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="883d3-145">Example</span></span>  
 <span data-ttu-id="883d3-146">Aşağıdaki örnek, geçersiz kutudan çıkarma, söz konusu ve elde edilen gösterir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="883d3-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="883d3-147">Kullanarak `try` ve `catch`, hata oluştuğunda hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="883d3-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 <span data-ttu-id="883d3-148">Bu program çıkarır:</span><span class="sxs-lookup"><span data-stu-id="883d3-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="883d3-149">Deyim değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="883d3-149">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="883d3-150">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="883d3-150">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="883d3-151">dönüştürme gerçekleştirilir ve çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="883d3-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="883d3-152">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="883d3-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="883d3-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="883d3-153">Related Sections</span></span>  
 <span data-ttu-id="883d3-154">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="883d3-154">For more information:</span></span>  
  
-   [<span data-ttu-id="883d3-155">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="883d3-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="883d3-156">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="883d3-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="883d3-157">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="883d3-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="883d3-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="883d3-158">See Also</span></span>  
 [<span data-ttu-id="883d3-159">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="883d3-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

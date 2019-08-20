---
title: Kutulama ve kutudan çıkarma C# -Programlama Kılavuzu
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
ms.openlocfilehash: 849983bb9cce6c9e0f41247a898747300fd29435
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588529"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="e0d28-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e0d28-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="e0d28-103">Kutulama, bir [değer türünü](../../language-reference/keywords/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-103">Boxing is the process of converting a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="e0d28-104">CLR bir değer türüne sahip olduğunda, değeri bir <xref:System.Object?displayProperty=nameWithType> örnek içinde sarmalar ve yönetilen yığında depolar.</span><span class="sxs-lookup"><span data-stu-id="e0d28-104">When the CLR boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="e0d28-105">Kutudan çıkarma, nesneden değer türünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="e0d28-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="e0d28-106">Paketleme örtük; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="e0d28-107">Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki C# değerin bir nesne olarak değerlendiribileceği tür sisteminin Birleşik görünümünü içermez.</span><span class="sxs-lookup"><span data-stu-id="e0d28-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="e0d28-108">Aşağıdaki örnekte, tamsayı değişkeni `i` paketlenmelidir ve nesnesine `o`atanır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="e0d28-109">Nesne `o` daha sonra kutulanabilir ve tamsayı değişkenine `i`atanabilir:</span><span class="sxs-lookup"><span data-stu-id="e0d28-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="e0d28-110">Aşağıdaki örnekler, kutulamayı ' de C#nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="e0d28-111">Performans</span><span class="sxs-lookup"><span data-stu-id="e0d28-111">Performance</span></span>  
 <span data-ttu-id="e0d28-112">Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="e0d28-113">Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="e0d28-114">Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur.</span><span class="sxs-lookup"><span data-stu-id="e0d28-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="e0d28-115">Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="e0d28-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="e0d28-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="e0d28-116">Boxing</span></span>  
 <span data-ttu-id="e0d28-117">Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="e0d28-118">Kutulama, bir [değer türünün](../../language-reference/keywords/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük olarak dönüştürülmedir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-118">Boxing is an implicit conversion of a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="e0d28-119">Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e0d28-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="e0d28-120">Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e0d28-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="e0d28-121">Aşağıdaki ifade, değişkende `i`kutulama işlemini örtülü olarak uygular:</span><span class="sxs-lookup"><span data-stu-id="e0d28-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="e0d28-122">Bu deyimin sonucu, yığında, yığında tür `o` `int`değerine başvuran bir nesne başvurusu oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="e0d28-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="e0d28-123">Bu değer, değişkene `i`atanan değer türü değerinin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="e0d28-124">İki değişken `i` arasındaki fark, ve `o`aşağıdaki kutulama dönüştürme görüntüsünde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e0d28-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>  
  
 ![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 <span data-ttu-id="e0d28-126">Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="e0d28-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="e0d28-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d28-127">Description</span></span>  
 <span data-ttu-id="e0d28-128">Bu örnek, kutulama kullanarak bir `i` tamsayı değişkenini nesnesine `o` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e0d28-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="e0d28-129">Ardından, değişkeninde `i` depolanan değer ' `456`dan `123` ' a değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="e0d28-130">Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0d28-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0d28-131">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="e0d28-132">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e0d28-132">Unboxing</span></span>  
 <span data-ttu-id="e0d28-133">Kutudan çıkarma, türden `object` bir [değer türüne](../../language-reference/keywords/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüşümtür.</span><span class="sxs-lookup"><span data-stu-id="e0d28-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="e0d28-134">Kutudan çıkarma işlemi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="e0d28-134">An unboxing operation consists of:</span></span>  
  
- <span data-ttu-id="e0d28-135">Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="e0d28-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
- <span data-ttu-id="e0d28-136">Değer, örnekten değer türü değişkenine kopyalanıyor.</span><span class="sxs-lookup"><span data-stu-id="e0d28-136">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="e0d28-137">Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="e0d28-137">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="e0d28-138">Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e0d28-138">The following figure demonstrates the result of the previous statements:</span></span> 
  
 ![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 <span data-ttu-id="e0d28-140">Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d28-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="e0d28-141">Bir kaldırma `null` girişimi bir <xref:System.NullReferenceException>olur.</span><span class="sxs-lookup"><span data-stu-id="e0d28-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="e0d28-142">Uyumsuz bir değer türüne başvurunun kaldırılması denenmeye neden olur <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="e0d28-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0d28-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0d28-143">Example</span></span>  
 <span data-ttu-id="e0d28-144">Aşağıdaki örnek, geçersiz kutudan çıkarma ve sonuç olarak ortaya çıkan `InvalidCastException`bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="e0d28-145">`try` Ve`catch`kullanarak, hata oluştuğunda bir hata mesajı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0d28-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="e0d28-146">Bu program çıkışlar:</span><span class="sxs-lookup"><span data-stu-id="e0d28-146">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="e0d28-147">İfadesini değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="e0d28-147">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="e0d28-148">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="e0d28-148">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="e0d28-149">dönüştürme gerçekleştirilecek ve şu çıktıyı alacaksınız:</span><span class="sxs-lookup"><span data-stu-id="e0d28-149">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="e0d28-150">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e0d28-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="e0d28-151">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0d28-151">Related Sections</span></span>  
 <span data-ttu-id="e0d28-152">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="e0d28-152">For more information:</span></span>  
  
- [<span data-ttu-id="e0d28-153">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="e0d28-153">Reference Types</span></span>](../../language-reference/keywords/reference-types.md)  
  
- [<span data-ttu-id="e0d28-154">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="e0d28-154">Value Types</span></span>](../../language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0d28-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d28-155">See also</span></span>

- [<span data-ttu-id="e0d28-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0d28-156">C# Programming Guide</span></span>](../index.md)

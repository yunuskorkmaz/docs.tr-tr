---
title: Kutulama ve kutudan çıkarma-C# Programlama Kılavuzu
description: C# programlamada kutulama ve kutudan çıkarma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5a5bfcc79de8ba3ff66ca8aab9d86d69d89f9221
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380702"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="d099d-104">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d099d-104">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="d099d-105">Kutulama, bir [değer türünü](../../language-reference/builtin-types/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d099d-105">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="d099d-106">Ortak dil çalışma zamanı (CLR) bir değer türüne sahip olduğunda, değeri bir örnek içinde sarmalar <xref:System.Object?displayProperty=nameWithType> ve yönetilen yığında depolar.</span><span class="sxs-lookup"><span data-stu-id="d099d-106">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="d099d-107">Kutudan çıkarma, nesneden değer türünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="d099d-107">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="d099d-108">Paketleme örtük; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="d099d-108">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="d099d-109">Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki değerin bir nesne olarak değerlendiribileceği tür sisteminin C# Birleşik görünümünü içermez.</span><span class="sxs-lookup"><span data-stu-id="d099d-109">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="d099d-110">Aşağıdaki örnekte, tamsayı değişkeni `i` *paketlenmelidir* ve nesnesine atanır `o` .</span><span class="sxs-lookup"><span data-stu-id="d099d-110">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="d099d-111">Nesne `o` daha sonra kutulanabilir ve tamsayı değişkenine atanabilir `i` :</span><span class="sxs-lookup"><span data-stu-id="d099d-111">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="d099d-112">Aşağıdaki örneklerde, kutulamayı C# ' de nasıl kullandığınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d099d-112">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="d099d-113">Performans</span><span class="sxs-lookup"><span data-stu-id="d099d-113">Performance</span></span>

<span data-ttu-id="d099d-114">Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="d099d-114">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="d099d-115">Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d099d-115">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="d099d-116">Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur.</span><span class="sxs-lookup"><span data-stu-id="d099d-116">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="d099d-117">Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="d099d-117">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="d099d-118">Kutulama</span><span class="sxs-lookup"><span data-stu-id="d099d-118">Boxing</span></span>

<span data-ttu-id="d099d-119">Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d099d-119">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="d099d-120">Kutulama, bir [değer türünün](../../language-reference/builtin-types/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük olarak dönüştürülmedir.</span><span class="sxs-lookup"><span data-stu-id="d099d-120">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="d099d-121">Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="d099d-121">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="d099d-122">Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d099d-122">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="d099d-123">Aşağıdaki ifade, değişkende kutulama işlemini örtülü olarak uygular `i` :</span><span class="sxs-lookup"><span data-stu-id="d099d-123">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="d099d-124">Bu deyimin sonucu, yığında, `o` yığında tür değerine başvuran bir nesne başvurusu oluşturuyor `int` .</span><span class="sxs-lookup"><span data-stu-id="d099d-124">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="d099d-125">Bu değer, değişkene atanan değer türü değerinin bir kopyasıdır `i` .</span><span class="sxs-lookup"><span data-stu-id="d099d-125">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="d099d-126">İki değişken arasındaki fark, `i` ve `o` aşağıdaki kutulama dönüştürme görüntüsünde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d099d-126">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="d099d-128">Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="d099d-128">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="d099d-129">Description</span><span class="sxs-lookup"><span data-stu-id="d099d-129">Description</span></span>

<span data-ttu-id="d099d-130">Bu örnek, kutulama kullanarak bir tamsayı değişkenini `i` nesnesine dönüştürür `o` .</span><span class="sxs-lookup"><span data-stu-id="d099d-130">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="d099d-131">Ardından, değişkeninde depolanan değer ' dan ' a `i` değiştirilir `123` `456` .</span><span class="sxs-lookup"><span data-stu-id="d099d-131">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="d099d-132">Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d099d-132">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="d099d-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d099d-133">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="d099d-134">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="d099d-134">Unboxing</span></span>

<span data-ttu-id="d099d-135">Kutudan çıkarma, türden `object` bir [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüşümtür.</span><span class="sxs-lookup"><span data-stu-id="d099d-135">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="d099d-136">Kutudan çıkarma işlemi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="d099d-136">An unboxing operation consists of:</span></span>

- <span data-ttu-id="d099d-137">Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="d099d-137">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="d099d-138">Değer, örnekten değer türü değişkenine kopyalanıyor.</span><span class="sxs-lookup"><span data-stu-id="d099d-138">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="d099d-139">Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d099d-139">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="d099d-140">Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d099d-140">The following figure demonstrates the result of the previous statements:</span></span>

![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="d099d-142">Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d099d-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="d099d-143">Bir kaldırma girişimi `null` bir olur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="d099d-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="d099d-144">Uyumsuz bir değer türüne başvurunun kaldırılması denenmeye neden olur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="d099d-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="d099d-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="d099d-145">Example</span></span>

<span data-ttu-id="d099d-146">Aşağıdaki örnek, geçersiz kutudan çıkarma ve sonuç olarak ortaya çıkan bir durumu gösterir `InvalidCastException` .</span><span class="sxs-lookup"><span data-stu-id="d099d-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="d099d-147">`try`Ve kullanarak `catch` , hata oluştuğunda bir hata mesajı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d099d-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="d099d-148">Bu program çıkışlar:</span><span class="sxs-lookup"><span data-stu-id="d099d-148">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="d099d-149">İfadesini değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="d099d-149">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="d099d-150">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="d099d-150">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="d099d-151">dönüştürme gerçekleştirilecek ve şu çıktıyı alacaksınız:</span><span class="sxs-lookup"><span data-stu-id="d099d-151">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="d099d-152">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d099d-152">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d099d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d099d-153">See also</span></span>

- [<span data-ttu-id="d099d-154">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d099d-154">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d099d-155">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="d099d-155">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="d099d-156">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="d099d-156">Value types</span></span>](../../language-reference/builtin-types/value-types.md)

---
title: Kutulama ve kutudan çıkarma C# -Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745418"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="10e98-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="10e98-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="10e98-103">Kutulama, bir [değer türünü](../../language-reference/builtin-types/value-types.md) tür `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="10e98-103">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="10e98-104">Ortak dil çalışma zamanı (CLR) bir değer türü olduğunda, değeri bir <xref:System.Object?displayProperty=nameWithType> örneği içinde sarmalanır ve yönetilen yığında depolar.</span><span class="sxs-lookup"><span data-stu-id="10e98-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="10e98-105">Kutudan çıkarma, nesneden değer türünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="10e98-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="10e98-106">Paketleme örtük; kutudan çıkarma açıktır.</span><span class="sxs-lookup"><span data-stu-id="10e98-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="10e98-107">Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki C# değerin bir nesne olarak değerlendiribileceği tür sisteminin Birleşik görünümünü içermez.</span><span class="sxs-lookup"><span data-stu-id="10e98-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="10e98-108">Aşağıdaki örnekte, `i` tamsayı değişkeni *paketlenmelidir* ve nesne `o`atanır.</span><span class="sxs-lookup"><span data-stu-id="10e98-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="10e98-109">Nesne `o` kutudan kutulanabilir ve tamsayı değişkenine atanabilir `i`:</span><span class="sxs-lookup"><span data-stu-id="10e98-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="10e98-110">Aşağıdaki örnekler, kutulamayı ' de C#nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10e98-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="10e98-111">Performans</span><span class="sxs-lookup"><span data-stu-id="10e98-111">Performance</span></span>

<span data-ttu-id="10e98-112">Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="10e98-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="10e98-113">Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10e98-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="10e98-114">Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur.</span><span class="sxs-lookup"><span data-stu-id="10e98-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="10e98-115">Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="10e98-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="10e98-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="10e98-116">Boxing</span></span>

<span data-ttu-id="10e98-117">Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10e98-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="10e98-118">Kutulama, `object` türüne veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük bir [değer türü](../../language-reference/builtin-types/value-types.md) dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="10e98-118">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="10e98-119">Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="10e98-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="10e98-120">Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="10e98-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="10e98-121">Aşağıdaki ifade, `i`değişkende kutulama işlemini örtülü olarak uygular:</span><span class="sxs-lookup"><span data-stu-id="10e98-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="10e98-122">Bu deyimin sonucu yığın üzerinde `o`bir nesne başvurusu oluşturuyor ve yığında `int`türünde bir değere başvuruda bulunur.</span><span class="sxs-lookup"><span data-stu-id="10e98-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="10e98-123">Bu değer, `i`değişkenine atanan değer türü değerinin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="10e98-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="10e98-124">`i` ve `o`iki değişken arasındaki fark, kutulama dönüştürme işleminin aşağıdaki görüntüsünde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="10e98-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="10e98-126">Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="10e98-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="10e98-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e98-127">Description</span></span>

<span data-ttu-id="10e98-128">Bu örnek, kutulama kullanarak bir `i` tamsayı değişkenini nesne `o` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="10e98-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="10e98-129">Daha sonra, `i` değişkende depolanan değer `123` `456`olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="10e98-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="10e98-130">Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10e98-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="10e98-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="10e98-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="10e98-132">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="10e98-132">Unboxing</span></span>

<span data-ttu-id="10e98-133">Kutudan çıkarma, tür `object` bir [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="10e98-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="10e98-134">Kutudan çıkarma işlemi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="10e98-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="10e98-135">Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="10e98-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="10e98-136">Değer, örnekten değer türü değişkenine kopyalanıyor.</span><span class="sxs-lookup"><span data-stu-id="10e98-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="10e98-137">Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="10e98-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="10e98-138">Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="10e98-138">The following figure demonstrates the result of the previous statements:</span></span>

![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="10e98-140">Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10e98-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="10e98-141">`null` kutudan çıkarılmaya çalışılması <xref:System.NullReferenceException>neden olur.</span><span class="sxs-lookup"><span data-stu-id="10e98-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="10e98-142">Uyumsuz bir değer türüne başvurunun kutudan çıkarılmaya çalışılması bir <xref:System.InvalidCastException>neden olur.</span><span class="sxs-lookup"><span data-stu-id="10e98-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="10e98-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="10e98-143">Example</span></span>

<span data-ttu-id="10e98-144">Aşağıdaki örnek, geçersiz kutudan çıkarma ve elde edilen `InvalidCastException`durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="10e98-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="10e98-145">`try` ve `catch`kullanarak, hata oluştuğunda bir hata mesajı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10e98-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="10e98-146">Bu program çıkışlar:</span><span class="sxs-lookup"><span data-stu-id="10e98-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="10e98-147">İfadesini değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="10e98-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="10e98-148">Yeni değer:</span><span class="sxs-lookup"><span data-stu-id="10e98-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="10e98-149">dönüştürme gerçekleştirilecek ve şu çıktıyı alacaksınız:</span><span class="sxs-lookup"><span data-stu-id="10e98-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="10e98-150">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="10e98-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10e98-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10e98-151">See also</span></span>

- [<span data-ttu-id="10e98-152">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="10e98-152">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="10e98-153">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="10e98-153">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="10e98-154">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="10e98-154">Value types</span></span>](../../language-reference/builtin-types/value-types.md)

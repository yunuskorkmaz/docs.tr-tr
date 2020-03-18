---
title: Boks ve Unboxing - C# Programlama Kılavuzu
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745418"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="aeb41-102">Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="aeb41-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="aeb41-103">Kutulama, bir değer [türünü](../../language-reference/builtin-types/value-types.md) bu değer `object` türü tarafından uygulanan türe veya herhangi bir arabirim türüne dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-103">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="aeb41-104">Ortak dil çalışma zamanı (CLR) bir değer türünü kutular, <xref:System.Object?displayProperty=nameWithType> bir örneğin içindeki değeri sarar ve yönetilen yığında depolar.</span><span class="sxs-lookup"><span data-stu-id="aeb41-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="aeb41-105">Unboxing nesneden değer türünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="aeb41-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="aeb41-106">Boks örtülüdür; unboxing açıktır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="aeb41-107">Kutulama ve unboxing kavramı, herhangi bir türde bir değerin nesne olarak kabul edilebildiği tür sisteminin C# birleşik görünümünün altında yatan temeldir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="aeb41-108">Aşağıdaki örnekte, aynık değişkeni `i` *kutulanır* ve `o`nesneye atanır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="aeb41-109">Nesne `o` daha sonra kutudan çözülebilir ve sonda değişkenine `i`atanabilir:</span><span class="sxs-lookup"><span data-stu-id="aeb41-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="aeb41-110">Aşağıdaki örnekler, c#'da kutulamanın nasıl kullanıldığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="aeb41-111">Performans</span><span class="sxs-lookup"><span data-stu-id="aeb41-111">Performance</span></span>

<span data-ttu-id="aeb41-112">Basit atamalarla ilgili olarak, kutulama ve unboxing hesaplama açısından pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="aeb41-113">Bir değer türü kutulandığında, yeni bir nesne tahsis edilmeli ve oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="aeb41-114">Daha az bir dereceye kadar, unboxing için gerekli döküm de hesaplama pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="aeb41-115">Daha fazla bilgi için [Performans'a](../../../framework/performance/performance-tips.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb41-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="aeb41-116">Kutulama</span><span class="sxs-lookup"><span data-stu-id="aeb41-116">Boxing</span></span>

<span data-ttu-id="aeb41-117">Kutulama, çöp toplanmış yığında değer türlerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="aeb41-118">Kutulama, bir [değer türünün](../../language-reference/builtin-types/value-types.md) bu `object` değer türü tarafından uygulanan türe veya herhangi bir arabirim türüne örtülü olarak dönüştürülmesidir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-118">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="aeb41-119">Bir değer türünü kutuya bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="aeb41-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="aeb41-120">Değer türü değişkeninaşağıdaki bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="aeb41-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="aeb41-121">Aşağıdaki ifade, değişken `i`üzerinde kutulama işlemini zımni olarak uygular:</span><span class="sxs-lookup"><span data-stu-id="aeb41-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="aeb41-122">Bu deyimin sonucu, yığınüzerinde, yığınüzerinde, tür `o` `int`, bir değer başvurulan bir nesne başvurusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aeb41-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="aeb41-123">Bu değer, değişkene `i`atanan değer türü değerinin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb41-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="aeb41-124">İki değişken arasındaki fark `i` ve `o`, kutulama dönüştürme aşağıdaki resimde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aeb41-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![I ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="aeb41-126">Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="aeb41-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="aeb41-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeb41-127">Description</span></span>

<span data-ttu-id="aeb41-128">Bu örnek, bir tamsayı `i` değişkenini kutulama kullanarak bir nesneye `o` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="aeb41-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="aeb41-129">Daha sonra, değişkende `i` depolanan değer `123` `456`' den ' e değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="aeb41-130">Örnek, özgün değer türünün ve kutulanan nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depolayabildiği ni gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="aeb41-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeb41-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="aeb41-132">Kutulama</span><span class="sxs-lookup"><span data-stu-id="aeb41-132">Unboxing</span></span>

<span data-ttu-id="aeb41-133">Unboxing, türden `object` [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="aeb41-134">Bir unboxing işlemi oluşur:</span><span class="sxs-lookup"><span data-stu-id="aeb41-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="aeb41-135">Verilen değer türünün kutulanmış bir değeri olduğundan emin olmak için nesne örneğini denetleme.</span><span class="sxs-lookup"><span data-stu-id="aeb41-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="aeb41-136">Örnekteki değeri değer türü değişkenine kopyalama.</span><span class="sxs-lookup"><span data-stu-id="aeb41-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="aeb41-137">Aşağıdaki ifadeler hem kutulama hem de unboxing işlemlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="aeb41-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="aeb41-138">Aşağıdaki şekil önceki ifadelerin sonucunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="aeb41-138">The following figure demonstrates the result of the previous statements:</span></span>

![Kutulama dönüştürmeyi gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="aeb41-140">Değer türlerinin zaman içinde başarılı olabilmesi için, kutusuz olan öğenin daha önce bu değer türünden bir örneğin kutulatılarak oluşturulan bir nesneye başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="aeb41-141">Kutusunu `null` kaldırmaya çalışmak bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="aeb41-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="aeb41-142">Uyumsuz bir değer türüne başvuruyu kaldırmaya çalışmak <xref:System.InvalidCastException>bir .</span><span class="sxs-lookup"><span data-stu-id="aeb41-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="aeb41-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeb41-143">Example</span></span>

<span data-ttu-id="aeb41-144">Aşağıdaki örnek, geçersiz bir kutulama ve ortaya `InvalidCastException`çıkan bir durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="aeb41-145">Hata `try` `catch`oluştuğunda bir hata iletisi kullanarak ve , bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aeb41-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="aeb41-146">Bu program çıktıları:</span><span class="sxs-lookup"><span data-stu-id="aeb41-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="aeb41-147">İfadeyi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="aeb41-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="aeb41-148">yerine şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="aeb41-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="aeb41-149">dönüştürme gerçekleştirilir ve çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="aeb41-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="aeb41-150">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aeb41-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aeb41-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb41-151">See also</span></span>

- [<span data-ttu-id="aeb41-152">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aeb41-152">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="aeb41-153">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="aeb41-153">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="aeb41-154">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="aeb41-154">Value types</span></span>](../../language-reference/builtin-types/value-types.md)

---
title: İşaretçi türleri - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507041"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="c7431-102">İşaretçi türleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c7431-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="c7431-103">Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="c7431-104">Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="c7431-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="c7431-105">İşaretçi türünden `*` önce belirtilen türe **başvuru türü**denir.</span><span class="sxs-lookup"><span data-stu-id="c7431-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="c7431-106">Yalnızca [yönetilmeyen](../../language-reference/builtin-types/unmanaged-types.md) bir tür başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="c7431-107">İşaretçi türleri [nesneden](../../language-reference/builtin-types/reference-types.md) devralmaz ve işaretçi `object`türleri arasında dönüşüm yoktur ve .</span><span class="sxs-lookup"><span data-stu-id="c7431-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="c7431-108">Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c7431-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="c7431-109">Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7431-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="c7431-110">Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (\*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c7431-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="c7431-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c7431-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="c7431-112">Bir işaretçi başvuruyu veya başvuru içeren bir [yapıyı](../../language-reference/builtin-types/struct.md) işaret edemez, çünkü bir nesne başvurusu işaret çikarsa bile bir nesne başvurusu çöp olarak toplanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-112">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="c7431-113">Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.</span><span class="sxs-lookup"><span data-stu-id="c7431-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="c7431-114">Tür işaretçi değişkeninin `myType*` değeri, türdeki `myType`bir değişkenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="c7431-115">Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c7431-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="c7431-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7431-116">Example</span></span>|<span data-ttu-id="c7431-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7431-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="c7431-118">`p`bir tamsayı için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="c7431-119">`p`bir tamsayı için işaretçi dir.</span><span class="sxs-lookup"><span data-stu-id="c7431-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="c7431-120">`p`tamsayılar için işaretçilerin tek boyutlu bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="c7431-121">`p`bir char için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="c7431-122">`p`bilinmeyen bir türe işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="c7431-123">İşaretçi yöneltme işleci \*, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="c7431-124">Örneğin, aşağıdaki bildirimi ele alalım:</span><span class="sxs-lookup"><span data-stu-id="c7431-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="c7431-125">İfade, `*myVariable` `myVariable`'' `int` adresinde bulunan değişkeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7431-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="c7431-126">Konular [sabit İfade](../../language-reference/keywords/fixed-statement.md) ve [İşaretçi Dönüşümleri](./pointer-conversions.md)işaretçileri birkaç örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="c7431-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="c7431-127">Aşağıdaki örnekte `unsafe` anahtar kelime `fixed` ve deyim kullanır ve bir iç işaretçi nasıl artış gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7431-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="c7431-128">Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7431-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="c7431-129">Bu örnekler [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği kümesi ile derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c7431-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="c7431-130">Yön işleci, bir tür `void*`işaretçisine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c7431-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="c7431-131">Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7431-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="c7431-132">Bir işaretçi `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-132">A pointer can be `null`.</span></span> <span data-ttu-id="c7431-133">Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7431-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="c7431-134">İşaretçileri yöntemler arasında geçirme, tanımlanmamış davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7431-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="c7431-135">Bir işaretçiyi yerel bir değişkene `in`, `out`bir `ref` parametre veya işlev sonucu olarak döndüren bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="c7431-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="c7431-136">İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.</span><span class="sxs-lookup"><span data-stu-id="c7431-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="c7431-137">Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="c7431-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="c7431-138">İşleç/Deyim</span><span class="sxs-lookup"><span data-stu-id="c7431-138">Operator/Statement</span></span>|<span data-ttu-id="c7431-139">Kullanım</span><span class="sxs-lookup"><span data-stu-id="c7431-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="c7431-140">İşaretçi yöneltmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7431-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="c7431-141">Bir yapının bir üyesine bir işaretçi yoluyla erişir.</span><span class="sxs-lookup"><span data-stu-id="c7431-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="c7431-142">Bir işaretçiyi dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="c7431-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="c7431-143">Bir değişkenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="c7431-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="c7431-144">`++` ve `--`</span><span class="sxs-lookup"><span data-stu-id="c7431-144">`++` and `--`</span></span>|<span data-ttu-id="c7431-145">İşaretçileri artırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="c7431-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="c7431-146">`+` ve `-`</span><span class="sxs-lookup"><span data-stu-id="c7431-146">`+` and `-`</span></span>|<span data-ttu-id="c7431-147">İşaretçi aritmetiği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7431-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="c7431-148">`==`, `!=` `<`, `>` `<=`, , ve`>=`</span><span class="sxs-lookup"><span data-stu-id="c7431-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="c7431-149">İşaretçileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7431-149">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="c7431-150">Yığında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="c7431-150">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="c7431-151">`fixed`Deyim</span><span class="sxs-lookup"><span data-stu-id="c7431-151">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="c7431-152">Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.</span><span class="sxs-lookup"><span data-stu-id="c7431-152">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="c7431-153">İşaretçi yle ilgili işleçler hakkında daha fazla bilgi için [Işaretçi ile ilgili işleçler'e](../../language-reference/operators/pointer-related-operators.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c7431-153">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7431-154">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c7431-154">C# language specification</span></span>

<span data-ttu-id="c7431-155">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Pointer türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c7431-155">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7431-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7431-156">See also</span></span>

- [<span data-ttu-id="c7431-157">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7431-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7431-158">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="c7431-158">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="c7431-159">İşaretçi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c7431-159">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="c7431-160">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="c7431-160">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="c7431-161">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="c7431-161">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="c7431-162">Güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="c7431-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)

---
title: İşaretçi türleri-C# Programlama Kılavuzu
description: İşaretçi türleri hakkında bilgi edinin. Farklı işaretçiler, kod örnekleri ve diğer kullanılabilir kaynakları görüntüleme örneklerine bakın.
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 9c62a31f9a4a090fe56fb10ac45fe2f93f1b036e
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382041"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="e6505-104">İşaretçi türleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e6505-104">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="e6505-105">Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6505-105">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="e6505-106">Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="e6505-106">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="e6505-107">`*`Bir işaretçi türündeki öğesinden önce belirtilen tür, **başvurulan tür**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e6505-107">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="e6505-108">Yalnızca [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md) , başvurulan bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6505-108">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="e6505-109">İşaretçi türleri [nesneden](../../language-reference/builtin-types/reference-types.md) aktarılmaz ve işaretçi türleri ve arasında dönüştürme yok `object` .</span><span class="sxs-lookup"><span data-stu-id="e6505-109">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="e6505-110">Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e6505-110">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="e6505-111">Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6505-111">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="e6505-112">Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (\*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e6505-112">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="e6505-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e6505-113">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="e6505-114">Bir işaretçi, bir işaretçiye işaret eden bir nesne başvurusu atık olarak toplanabileceğinden, bir başvuruya veya başvuru içeren bir [yapıya](../../language-reference/builtin-types/struct.md) işaret edemez.</span><span class="sxs-lookup"><span data-stu-id="e6505-114">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="e6505-115">Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.</span><span class="sxs-lookup"><span data-stu-id="e6505-115">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="e6505-116">Türündeki işaretçi değişkeninin değeri, `myType*` türünde bir değişkenin adresidir `myType` .</span><span class="sxs-lookup"><span data-stu-id="e6505-116">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="e6505-117">Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e6505-117">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="e6505-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6505-118">Example</span></span>|<span data-ttu-id="e6505-119">Description</span><span class="sxs-lookup"><span data-stu-id="e6505-119">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="e6505-120">`p`bir tamsayıya yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="e6505-120">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="e6505-121">`p`, tamsayıya yönelik işaretçinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="e6505-121">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="e6505-122">`p`, tamsayılara yönelik işaretçilerin tek boyutlu bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="e6505-122">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="e6505-123">`p`, Char için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="e6505-123">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="e6505-124">`p`, bilinmeyen bir türe yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="e6505-124">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="e6505-125">İşaretçi yöneltme işleci \*, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e6505-125">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="e6505-126">Örneğin, aşağıdaki bildirimi ele alalım:</span><span class="sxs-lookup"><span data-stu-id="e6505-126">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="e6505-127">İfade, `*myVariable` içinde bulunan `int` adreste bulunan değişkeni gösterir `myVariable` .</span><span class="sxs-lookup"><span data-stu-id="e6505-127">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="e6505-128">Konular [Sabit bildiriminde](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüştürmelerinde birçok işaretçiye](./pointer-conversions.md)örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="e6505-128">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="e6505-129">Aşağıdaki örnek, `unsafe` anahtar sözcüğünü ve ifadesini kullanır `fixed` ve iç işaretçinin nasıl artırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6505-129">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="e6505-130">Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6505-130">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="e6505-131">Bu örneklerin [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçenek kümesiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6505-131">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

<span data-ttu-id="e6505-132">Yöneltme işlecini türündeki bir işaretçiye uygulayamazsınız `void*` .</span><span class="sxs-lookup"><span data-stu-id="e6505-132">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="e6505-133">Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6505-133">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="e6505-134">Bir işaretçi olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="e6505-134">A pointer can be `null`.</span></span> <span data-ttu-id="e6505-135">Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="e6505-135">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="e6505-136">Yöntemler arasında işaretçiler geçirmek tanımsız davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6505-136">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="e6505-137">Bir `in` , `out` veya `ref` parametresi ya da işlev sonucu olarak yerel bir değişkene bir işaretçi döndüren bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="e6505-137">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="e6505-138">İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.</span><span class="sxs-lookup"><span data-stu-id="e6505-138">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="e6505-139">Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="e6505-139">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="e6505-140">İşleç/Deyim</span><span class="sxs-lookup"><span data-stu-id="e6505-140">Operator/Statement</span></span>|<span data-ttu-id="e6505-141">Kullanın</span><span class="sxs-lookup"><span data-stu-id="e6505-141">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="e6505-142">İşaretçi yöneltmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e6505-142">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="e6505-143">Bir yapının bir üyesine bir işaretçi yoluyla erişir.</span><span class="sxs-lookup"><span data-stu-id="e6505-143">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="e6505-144">Bir işaretçiyi dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="e6505-144">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="e6505-145">Bir değişkenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e6505-145">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="e6505-146">`++` ve `--`</span><span class="sxs-lookup"><span data-stu-id="e6505-146">`++` and `--`</span></span>|<span data-ttu-id="e6505-147">İşaretçileri artırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="e6505-147">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="e6505-148">`+` ve `-`</span><span class="sxs-lookup"><span data-stu-id="e6505-148">`+` and `-`</span></span>|<span data-ttu-id="e6505-149">İşaretçi aritmetiği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e6505-149">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="e6505-150">`==`, `!=` , `<` , `>` , `<=` ve`>=`</span><span class="sxs-lookup"><span data-stu-id="e6505-150">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="e6505-151">İşaretçileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e6505-151">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="e6505-152">Yığında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="e6505-152">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="e6505-153">`fixed`Ekstre</span><span class="sxs-lookup"><span data-stu-id="e6505-153">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="e6505-154">Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.</span><span class="sxs-lookup"><span data-stu-id="e6505-154">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="e6505-155">İşaretçi ile ilgili işleçler hakkında daha fazla bilgi için bkz. [işaretçi ile ilgili işleçler](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e6505-155">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e6505-156">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e6505-156">C# language specification</span></span>

<span data-ttu-id="e6505-157">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e6505-157">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6505-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6505-158">See also</span></span>

- [<span data-ttu-id="e6505-159">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e6505-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6505-160">Güvenli olmayan kod ve Işaretçiler</span><span class="sxs-lookup"><span data-stu-id="e6505-160">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="e6505-161">İşaretçi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="e6505-161">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="e6505-162">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="e6505-162">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="e6505-163">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="e6505-163">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="e6505-164">olmayabilecek</span><span class="sxs-lookup"><span data-stu-id="e6505-164">unsafe</span></span>](../../language-reference/keywords/unsafe.md)

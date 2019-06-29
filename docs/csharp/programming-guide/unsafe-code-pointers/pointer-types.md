---
title: İşaretçi türleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 81e9a86c4761b329918bf04023dea42d2e1ad6f5
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423521"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="1cb15-102">İşaretçi türleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1cb15-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="1cb15-103">Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="1cb15-104">Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="1cb15-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="1cb15-105">Önce belirtilen tür `*` bir işaretçi türü olarak adlandırılır **başvurulan türü**.</span><span class="sxs-lookup"><span data-stu-id="1cb15-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="1cb15-106">Aşağıdaki türlerde herhangi bir grup türü olabilir:</span><span class="sxs-lookup"><span data-stu-id="1cb15-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="1cb15-107">Herhangi bir tamsayı türü: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [bayt](../../language-reference/builtin-types/integral-numeric-types.md), [kısa](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [uzun](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-107">Any integral type: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="1cb15-108">Herhangi bir kayan nokta türü: [float](../../language-reference/keywords/float.md), [çift](../../language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-108">Any floating-point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="1cb15-109">[char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="1cb15-110">[bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="1cb15-111">[ondalık](../../language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="1cb15-112">Tüm [enum](../../language-reference/keywords/enum.md) türü.</span><span class="sxs-lookup"><span data-stu-id="1cb15-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="1cb15-113">Herhangi bir işaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="1cb15-113">Any pointer type.</span></span> <span data-ttu-id="1cb15-114">Bu ifadeler gibi sağlar `void**`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="1cb15-115">Yalnızca yönetilmeyen türlerde alanlar içeren, kullanıcı tarafından tanımlanmış herhangi bir yapı türü.</span><span class="sxs-lookup"><span data-stu-id="1cb15-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="1cb15-116">İşaretçi türleri öğesinden devralmaz [nesne](../../language-reference/keywords/object.md) ve işaretçi türleri arasında dönüştürme işlemi yok var ve `object`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="1cb15-117">Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1cb15-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="1cb15-118">Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="1cb15-119">Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (\*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="1cb15-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1cb15-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="1cb15-121">Bir işaretçi, başvuru veya çok işaret edemez bir [yapı](../../language-reference/keywords/struct.md) bir nesne başvurusu bir işaretçi kendisine işaret ettiği bile çöpten toplanmış olabileceğinden başvurular içeren.</span><span class="sxs-lookup"><span data-stu-id="1cb15-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="1cb15-122">Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.</span><span class="sxs-lookup"><span data-stu-id="1cb15-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="1cb15-123">Türündeki işaretçi değişkeninin değerini `myType*` türünde bir değişkenin adresidir `myType`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="1cb15-124">Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1cb15-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="1cb15-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cb15-125">Example</span></span>|<span data-ttu-id="1cb15-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1cb15-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="1cb15-127">`p` bir tamsayının bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="1cb15-128">`p` bir tamsayı işaretçisi için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="1cb15-129">`p` işaretçileri dizisidir tek boyutlu bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="1cb15-130">`p` bir karakterin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="1cb15-131">`p` Bilinmeyen bir türün bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="1cb15-132">İşaretçi yöneltme işleci \*, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="1cb15-133">Örneğin, aşağıdaki bildirimi ele alalım:</span><span class="sxs-lookup"><span data-stu-id="1cb15-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="1cb15-134">İfade `*myVariable` gösterir `int` yer alan adreste bulunan değişkeni `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="1cb15-135">Çeşitli konularda işaretçi örnekleri vardır [fixed Statement](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüşümleri](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="1cb15-136">Aşağıdaki örnekte `unsafe` anahtar sözcüğü ve `fixed` ifadesi ve bir iç işaretçinin nasıl artırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="1cb15-137">Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="1cb15-138">Bu örnekler ile derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="1cb15-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="1cb15-139">Yöneltme işleci türünde bir işaretçiye uygulayamazsınız `void*`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="1cb15-140">Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="1cb15-141">Bir işaretçi olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="1cb15-141">A pointer can be `null`.</span></span> <span data-ttu-id="1cb15-142">Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="1cb15-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="1cb15-143">İşaretçilerin yöntemler arasında aktarılmasının tanımlanmamış davranışa neden.</span><span class="sxs-lookup"><span data-stu-id="1cb15-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="1cb15-144">Bir yerel değişken için bir işaretçi döndüren bir yöntem düşünün bir `in`, `out`, veya `ref` parametresi veya işlev sonucu olarak.</span><span class="sxs-lookup"><span data-stu-id="1cb15-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="1cb15-145">İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="1cb15-146">Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="1cb15-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="1cb15-147">İşleç/Deyim</span><span class="sxs-lookup"><span data-stu-id="1cb15-147">Operator/Statement</span></span>|<span data-ttu-id="1cb15-148">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="1cb15-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="1cb15-149">İşaretçi yöneltmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="1cb15-150">Bir yapının bir üyesine bir işaretçi yoluyla erişir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="1cb15-151">Bir işaretçiyi dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="1cb15-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="1cb15-152">Bir değişkenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1cb15-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="1cb15-153">`++` ve `--`</span><span class="sxs-lookup"><span data-stu-id="1cb15-153">`++` and `--`</span></span>|<span data-ttu-id="1cb15-154">İşaretçileri artırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="1cb15-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="1cb15-155">`+` ve `-`</span><span class="sxs-lookup"><span data-stu-id="1cb15-155">`+` and `-`</span></span>|<span data-ttu-id="1cb15-156">İşaretçi aritmetiği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cb15-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="1cb15-157">`==`, `!=`, `<`, `>`, `<=`, ve `>=`</span><span class="sxs-lookup"><span data-stu-id="1cb15-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="1cb15-158">İşaretçileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="1cb15-158">Compares pointers.</span></span>|
|[<span data-ttu-id="1cb15-159">`stackalloc` İşleci</span><span class="sxs-lookup"><span data-stu-id="1cb15-159">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="1cb15-160">Yığında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="1cb15-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="1cb15-161">`fixed` Deyimi</span><span class="sxs-lookup"><span data-stu-id="1cb15-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="1cb15-162">Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.</span><span class="sxs-lookup"><span data-stu-id="1cb15-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="1cb15-163">İşaretçi hakkında daha fazla bilgi için bkz: ilgili işleçleri [işaretçi işleçleri ilgili](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1cb15-164">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1cb15-164">C# language specification</span></span>

<span data-ttu-id="1cb15-165">Daha fazla bilgi için [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1cb15-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cb15-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cb15-166">See also</span></span>

- [<span data-ttu-id="1cb15-167">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1cb15-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1cb15-168">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="1cb15-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="1cb15-169">İşaretçi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="1cb15-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="1cb15-170">Türler</span><span class="sxs-lookup"><span data-stu-id="1cb15-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="1cb15-171">unsafe</span><span class="sxs-lookup"><span data-stu-id="1cb15-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)

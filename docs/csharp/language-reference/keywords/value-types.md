---
title: Değer türleri - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 9907811a43f408020e2ee76621d4975a53945570
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424025"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="45d58-102">Değer türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="45d58-102">Value types (C# Reference)</span></span>

<span data-ttu-id="45d58-103">Değer türlerinin iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="45d58-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="45d58-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="45d58-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="45d58-105">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="45d58-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="45d58-106">Değer türleri'larının temel özellikleri</span><span class="sxs-lookup"><span data-stu-id="45d58-106">Main features of value types</span></span>

<span data-ttu-id="45d58-107">Bir değer türünde bir değişken türünde bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="45d58-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="45d58-108">Örneğin, bir değişken `int` türü, değer içerebilir `42`.</span><span class="sxs-lookup"><span data-stu-id="45d58-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="45d58-109">Bu, bir başvuru türü olarak da bilinen bir nesne örneği içeren bir başvuru türünün bir değişkeni farklıdır.</span><span class="sxs-lookup"><span data-stu-id="45d58-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="45d58-110">Bu değer, bir değişkene bir değer türü yeni bir değer atadığınızda, kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="45d58-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="45d58-111">Başvuru türünde bir değişken için yeni bir değer atadığınızda, başvuru kopyalanır, nesnenin kendisini değil.</span><span class="sxs-lookup"><span data-stu-id="45d58-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="45d58-112">Tüm değer türleri örtülü olarak türetilmiş <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45d58-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="45d58-113">Farklı başvuru türleri ile yeni bir tür bir değer türünden türetilemez.</span><span class="sxs-lookup"><span data-stu-id="45d58-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="45d58-114">Ancak, başvuru türleri, ister yapılar, arabirimler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d58-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="45d58-115">Değer türü değişkenler olamaz `null` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="45d58-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="45d58-116">Ancak, karşılık gelen değişkenleri [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md) olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="45d58-116">However, variables of the corresponding [nullable types](../../../csharp/programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="45d58-117">Varsayılan değer türü başlatan örtük parametresiz bir oluşturucu her değer türünde.</span><span class="sxs-lookup"><span data-stu-id="45d58-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="45d58-118">Değer türleri varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="45d58-119">Basit türler</span><span class="sxs-lookup"><span data-stu-id="45d58-119">Simple types</span></span>

<span data-ttu-id="45d58-120">*Basit türler* bir dizi önceden tanımlanmış bir yapı türü tarafından sağlanan C# ve aşağıdaki türleri oluşturan:</span><span class="sxs-lookup"><span data-stu-id="45d58-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="45d58-121">[Tam sayı türleri](../builtin-types/integral-numeric-types.md): tamsayı sayısal türleri ve [char](char.md) türü</span><span class="sxs-lookup"><span data-stu-id="45d58-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="45d58-122">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="45d58-122">Floating-point types</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="45d58-123">bool</span><span class="sxs-lookup"><span data-stu-id="45d58-123">bool</span></span>](bool.md)

<span data-ttu-id="45d58-124">Basit türler anahtar sözcükleri tanımlanır, ancak bu anahtar sözcükler yalnızca önceden tanımlanmış bir yapı türleri için diğer adlar <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="45d58-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="45d58-125">Örneğin, [int](../builtin-types/integral-numeric-types.md) bir diğer adıdır <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45d58-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45d58-126">Diğer adlar tam bir listesi için bkz. [yerleşik türler tablosu](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="45d58-127">Basit türler, bazı ek işlemler izin vermek, diğer yapı türlerden farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="45d58-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="45d58-128">Basit türler, değişmez değerleri kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="45d58-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="45d58-129">Örneğin, `'A'` bir sabit değer türü olan `char` ve `2001` bir sabit değer türü olan `int`.</span><span class="sxs-lookup"><span data-stu-id="45d58-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="45d58-130">Sabitler ile basit türler bildirebilirsiniz [const](const.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="45d58-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="45d58-131">Diğer yapı tür sabitleri mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="45d58-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="45d58-132">Sabit ifadeler, işlenenleri tüm basit tür sabit değerlerdir, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="45d58-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="45d58-133">Daha fazla bilgi için [basit türler](~/_csharplang/spec/types.md#simple-types) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="45d58-134">Değer türleri başlatma</span><span class="sxs-lookup"><span data-stu-id="45d58-134">Initializing value types</span></span>

<span data-ttu-id="45d58-135">C# dilinde yerel değişkenler, kullanılmadan önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45d58-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="45d58-136">Örneğin, aşağıdaki örnekte olduğu gibi başlatma olmadan yerel bir değişken bildirmeniz:</span><span class="sxs-lookup"><span data-stu-id="45d58-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="45d58-137">Bunu başlatılmadan önce kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="45d58-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="45d58-138">Aşağıdaki deyimi kullanarak başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="45d58-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="45d58-139">Bu ifade, aşağıdaki deyime eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="45d58-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="45d58-140">Elbette, bildirim ve başlatma aşağıdaki örneklerde gösterildiği gibi aynı deyimde olabilir:</span><span class="sxs-lookup"><span data-stu-id="45d58-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="45d58-141">– veya –</span><span class="sxs-lookup"><span data-stu-id="45d58-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="45d58-142">Kullanarak [yeni](../operators/new-operator.md) işleci belirli türün parametresiz oluşturucu çağırır ve varsayılan değer değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="45d58-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="45d58-143">Önceki örnekte, parametresiz bir oluşturucu değer atanmış `0` için `myInt`.</span><span class="sxs-lookup"><span data-stu-id="45d58-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="45d58-144">Varsayılan Oluşturucu çağırarak atanan değerler hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-144">For more information about values assigned by calling default constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="45d58-145">Kullanıcı tanımlı türler ile kullanın [yeni](../operators/new-operator.md) parametresiz bir oluşturucu çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="45d58-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="45d58-146">Örneğin, aşağıdaki deyim, parametresiz oluşturucu çağırır `Point` yapısı:</span><span class="sxs-lookup"><span data-stu-id="45d58-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="45d58-147">Bu çağrıdan sonra kesinlikle atanacak yapı olarak kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="45d58-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="45d58-148">Hakkında daha fazla bilgi için `new` işleci bkz [yeni](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="45d58-149">Sayısal türlerin çıktı biçimlendirme hakkında daha fazla bilgi için bkz: [sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="45d58-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45d58-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45d58-150">See also</span></span>

- [<span data-ttu-id="45d58-151">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="45d58-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45d58-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="45d58-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45d58-153">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="45d58-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="45d58-154">Türler</span><span class="sxs-lookup"><span data-stu-id="45d58-154">Types</span></span>](types.md)
- [<span data-ttu-id="45d58-155">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="45d58-155">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="45d58-156">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="45d58-156">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)

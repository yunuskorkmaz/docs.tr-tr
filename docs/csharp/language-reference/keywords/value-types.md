---
title: Değer türleri- C# başvuru
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 940d21bdd90d4594a39edc20283ca6a45ccf81fe
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422210"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="1add0-102">Değer türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="1add0-102">Value types (C# Reference)</span></span>

<span data-ttu-id="1add0-103">İki tür değer türü vardır:</span><span class="sxs-lookup"><span data-stu-id="1add0-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="1add0-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="1add0-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="1add0-105">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1add0-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="1add0-106">Değer türlerinin ana özellikleri</span><span class="sxs-lookup"><span data-stu-id="1add0-106">Main features of value types</span></span>

<span data-ttu-id="1add0-107">Değer türünde bir değişken, türün bir değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1add0-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="1add0-108">Örneğin, `int` türünün bir değişkeni `42`değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="1add0-109">Bu, bir nesne olarak da bilinen tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1add0-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="1add0-110">Değer türünde bir değişkene yeni bir değer atadığınızda, bu değer kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1add0-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="1add0-111">Başvuru türündeki bir değişkene yeni bir değer atadığınızda, başvuru nesnenin kendisi değil, kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1add0-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="1add0-112">Tüm değer türleri örtük olarak <xref:System.ValueType?displayProperty=nameWithType>türetilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1add0-113">Başvuru türlerinden farklı olarak, bir değer türünden yeni bir tür türemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1add0-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="1add0-114">Ancak, başvuru türleri gibi yapılar, arabirimler uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="1add0-115">Değer türü değişkenleri varsayılan olarak `null` olamaz.</span><span class="sxs-lookup"><span data-stu-id="1add0-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="1add0-116">Ancak, karşılık gelen [null yapılabilir değer türlerinin](../../programming-guide/nullable-types/index.md) değişkenleri `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-116">However, variables of the corresponding [nullable value types](../../programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="1add0-117">Her değer türünün, bu türün varsayılan değerini Başlatan örtük parametresiz bir Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="1add0-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="1add0-118">Değer türlerinin varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="1add0-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="1add0-119">Basit türler</span><span class="sxs-lookup"><span data-stu-id="1add0-119">Simple types</span></span>

<span data-ttu-id="1add0-120">*Basit türler* tarafından C# sunulan önceden tanımlanmış bir yapı türleri kümesidir ve aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1add0-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="1add0-121">[Integral türleri](../builtin-types/integral-numeric-types.md): tamsayı sayısal türleri ve [char](char.md) türü</span><span class="sxs-lookup"><span data-stu-id="1add0-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="1add0-122">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="1add0-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="1add0-123">bool</span><span class="sxs-lookup"><span data-stu-id="1add0-123">bool</span></span>](bool.md)

<span data-ttu-id="1add0-124">Basit türler anahtar sözcükler aracılığıyla tanımlanır, ancak bu anahtar sözcükler yalnızca <xref:System> ad alanındaki önceden tanımlanmış yapı türleri için diğer adlardır.</span><span class="sxs-lookup"><span data-stu-id="1add0-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="1add0-125">Örneğin, [int](../builtin-types/integral-numeric-types.md) bir <xref:System.Int32?displayProperty=nameWithType>diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="1add0-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1add0-126">Diğer adların tam listesi için bkz. [Yerleşik türler tablosu](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="1add0-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="1add0-127">Basit türler, bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="1add0-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="1add0-128">Basit türler, değişmez değerler kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="1add0-129">Örneğin, `'A'` türü `char` bir değişmez değerdir ve `2001` `int`türü bir değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="1add0-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="1add0-130">[Const](const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1add0-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="1add0-131">Diğer yapı türlerinin sabitlerinin olması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1add0-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="1add0-132">İşlenenleri hepsi basit tür sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1add0-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="1add0-133">Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [basit türler](~/_csharplang/spec/types.md#simple-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1add0-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="1add0-134">Değer türlerini başlatma</span><span class="sxs-lookup"><span data-stu-id="1add0-134">Initializing value types</span></span>

<span data-ttu-id="1add0-135">Yerel değişkenlerin kullanılmadan C# önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1add0-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="1add0-136">Örneğin, aşağıdaki örnekte olduğu gibi, başlatma olmadan yerel bir değişken bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1add0-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="1add0-137">Bunu, başlamadan önce kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1add0-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="1add0-138">Aşağıdaki ifadeyi kullanarak başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1add0-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="1add0-139">Bu ifade aşağıdaki ifadeye eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="1add0-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="1add0-140">Tabii ki, bildirimi ve başlatmayı aşağıdaki örneklerle aynı bildirimde bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1add0-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="1add0-141">veya</span><span class="sxs-lookup"><span data-stu-id="1add0-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="1add0-142">[New](../operators/new-operator.md) işlecini kullanmak, belirli türde parametresiz oluşturucuyu çağırır ve varsayılan değeri değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="1add0-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="1add0-143">Önceki örnekte, parametresiz Oluşturucu değeri `myInt``0` atanır.</span><span class="sxs-lookup"><span data-stu-id="1add0-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="1add0-144">Parametresiz oluşturucular çağırarak atanan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="1add0-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="1add0-145">Kullanıcı tanımlı türlerle, parametresiz oluşturucuyu çağırmak için [Yeni](../operators/new-operator.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1add0-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="1add0-146">Örneğin, aşağıdaki ifade `Point` yapısının parametresiz oluşturucusunu çağırır:</span><span class="sxs-lookup"><span data-stu-id="1add0-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="1add0-147">Bu çağrıdan sonra yapının kesin olarak atanması kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1add0-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="1add0-148">`new` işleci hakkında daha fazla bilgi için, bkz. [Yeni](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1add0-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="1add0-149">Sayısal türlerin çıkışını biçimlendirme hakkında daha fazla bilgi için bkz. [sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="1add0-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1add0-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1add0-150">See also</span></span>

- [<span data-ttu-id="1add0-151">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="1add0-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1add0-152">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1add0-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1add0-153">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1add0-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1add0-154">Türler</span><span class="sxs-lookup"><span data-stu-id="1add0-154">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="1add0-155">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1add0-155">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="1add0-156">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="1add0-156">Nullable value types</span></span>](../../programming-guide/nullable-types/index.md)

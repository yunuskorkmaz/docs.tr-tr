---
title: Değer türleri- C# başvuru
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 0ab9b6e089f5add9963ffae73e196643ad999763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712916"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="0cbad-102">Değer türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="0cbad-102">Value types (C# Reference)</span></span>

<span data-ttu-id="0cbad-103">İki tür değer türü vardır:</span><span class="sxs-lookup"><span data-stu-id="0cbad-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="0cbad-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="0cbad-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="0cbad-105">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-105">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="0cbad-106">Değer türlerinin ana özellikleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-106">Main features of value types</span></span>

<span data-ttu-id="0cbad-107">Değer türünde bir değişken, türün bir değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="0cbad-108">Örneğin, `int` türünün bir değişkeni `42`değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="0cbad-109">Bu, bir nesne olarak da bilinen tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="0cbad-110">Değer türünde bir değişkene yeni bir değer atadığınızda, bu değer kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="0cbad-111">Başvuru türündeki bir değişkene yeni bir değer atadığınızda, başvuru nesnenin kendisi değil, kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="0cbad-112">Tüm değer türleri örtük olarak <xref:System.ValueType?displayProperty=nameWithType>türetilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0cbad-113">Başvuru türlerinden farklı olarak, bir değer türünden yeni bir tür türemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cbad-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="0cbad-114">Ancak, başvuru türleri gibi yapılar, arabirimler uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="0cbad-115">Değer türü değişkenleri varsayılan olarak `null` olamaz.</span><span class="sxs-lookup"><span data-stu-id="0cbad-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="0cbad-116">Ancak, karşılık gelen [null yapılabilir değer türlerinin](../builtin-types/nullable-value-types.md) değişkenleri `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span></span>

<span data-ttu-id="0cbad-117">Her değer türünün, bu türün varsayılan değerini Başlatan örtük parametresiz bir Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="0cbad-118">Değer türlerinin varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="0cbad-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="0cbad-119">Basit türler</span><span class="sxs-lookup"><span data-stu-id="0cbad-119">Simple types</span></span>

<span data-ttu-id="0cbad-120">*Basit türler* tarafından C# sunulan önceden tanımlanmış bir yapı türleri kümesidir ve aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0cbad-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="0cbad-121">[Integral türleri](../builtin-types/integral-numeric-types.md): tamsayı sayısal türleri ve [char](../builtin-types/char.md) türü</span><span class="sxs-lookup"><span data-stu-id="0cbad-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](../builtin-types/char.md) type</span></span>
- [<span data-ttu-id="0cbad-122">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="0cbad-123">bool</span><span class="sxs-lookup"><span data-stu-id="0cbad-123">bool</span></span>](../builtin-types/bool.md)

<span data-ttu-id="0cbad-124">Basit türler anahtar sözcükler aracılığıyla tanımlanır, ancak bu anahtar sözcükler yalnızca <xref:System> ad alanındaki önceden tanımlanmış yapı türleri için diğer adlardır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="0cbad-125">Örneğin, [int](../builtin-types/integral-numeric-types.md) bir <xref:System.Int32?displayProperty=nameWithType>diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0cbad-126">Diğer adların tam listesi için bkz. [Yerleşik türler tablosu](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="0cbad-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="0cbad-127">Basit türler, bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="0cbad-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="0cbad-128">Basit türler, değişmez değerler kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="0cbad-129">Örneğin, `'A'` türü `char` bir değişmez değerdir ve `2001` `int`türü bir değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="0cbad-130">[Const](const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cbad-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="0cbad-131">Diğer yapı türlerinin sabitlerinin olması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="0cbad-132">İşlenenleri hepsi basit tür sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="0cbad-133">Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [basit türler](~/_csharplang/spec/types.md#simple-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cbad-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="0cbad-134">Değer türlerini başlatma</span><span class="sxs-lookup"><span data-stu-id="0cbad-134">Initializing value types</span></span>

<span data-ttu-id="0cbad-135">Yerel değişkenlerin kullanılmadan C# önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cbad-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="0cbad-136">Örneğin, aşağıdaki örnekte olduğu gibi, başlatma olmadan yerel bir değişken bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cbad-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="0cbad-137">Bunu, başlamadan önce kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0cbad-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="0cbad-138">Aşağıdaki ifadeyi kullanarak başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cbad-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="0cbad-139">Bu ifade aşağıdaki ifadeye eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="0cbad-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="0cbad-140">Tabii ki, bildirimi ve başlatmayı aşağıdaki örneklerle aynı bildirimde bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cbad-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="0cbad-141">–veya–</span><span class="sxs-lookup"><span data-stu-id="0cbad-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="0cbad-142">[New](../operators/new-operator.md) işlecini kullanmak, belirli türde parametresiz oluşturucuyu çağırır ve varsayılan değeri değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="0cbad-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="0cbad-143">Önceki örnekte, parametresiz Oluşturucu değeri `myInt``0` atanır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="0cbad-144">Parametresiz oluşturucular çağırarak atanan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="0cbad-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="0cbad-145">Kullanıcı tanımlı türlerle, parametresiz oluşturucuyu çağırmak için [Yeni](../operators/new-operator.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0cbad-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="0cbad-146">Örneğin, aşağıdaki ifade `Point` yapısının parametresiz oluşturucusunu çağırır:</span><span class="sxs-lookup"><span data-stu-id="0cbad-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="0cbad-147">Bu çağrıdan sonra yapının kesin olarak atanması kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0cbad-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="0cbad-148">`new` işleci hakkında daha fazla bilgi için, bkz. [Yeni](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0cbad-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="0cbad-149">Sayısal türlerin çıkışını biçimlendirme hakkında daha fazla bilgi için bkz. [sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="0cbad-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cbad-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cbad-150">See also</span></span>

- [<span data-ttu-id="0cbad-151">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="0cbad-151">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0cbad-152">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-152">C# keywords</span></span>](index.md)
- [<span data-ttu-id="0cbad-153">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-153">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="0cbad-154">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="0cbad-154">Nullable value types</span></span>](../builtin-types/nullable-value-types.md)

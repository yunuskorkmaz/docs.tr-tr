---
title: Numaralandırma türleri - C# referansı
description: Bir seçimi veya bir seçenek birleşimini temsil eden C# numaralandırma türleri hakkında bilgi edinin
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 15f5e9ccb1396277229ba935381812700f63ece8
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121150"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="59202-103">Numaralandırma türleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="59202-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="59202-104">Numaralandırma *türü* (veya *enum türü),* alttaki [integral sayısal](integral-numeric-types.md) türünün adlandırılmış sabitler kümesi tarafından tanımlanan bir [değer türüdür.](value-types.md)</span><span class="sxs-lookup"><span data-stu-id="59202-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="59202-105">Numaralandırma türünü tanımlamak için, anahtar `enum` kelimeyi kullanın ve *enum üyelerinin*adlarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="59202-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="59202-106">Varsayılan olarak, enum üyelerinin ilişkili sabit `int`değerleri tür; sıfırla başlarlar ve tanım metin sırasını takiben bir oranında artarlar.</span><span class="sxs-lookup"><span data-stu-id="59202-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="59202-107">Başka bir [integral sayısal](integral-numeric-types.md) türü, bir numaralandırma türünün altında yatan bir tür olarak açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59202-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="59202-108">Aşağıdaki örnekte görüldüğü gibi, ilişkili sabit değerleri de açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59202-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="59202-109">Numaralandırma türü tanımı içinde bir yöntem tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="59202-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="59202-110">Numaralandırma türüne işlevsellik eklemek için bir [uzantı yöntemi](../../programming-guide/classes-and-structs/extension-methods.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="59202-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="59202-111">Numaralandırma türünün `E` varsayılan değeri, sıfır karşılık gelen `(E)0`enum üyesi olmasa bile ifade tarafından üretilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="59202-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="59202-112">Birbirini dışlayan değerler kümesinden veya seçeneklerin birleşiminden bir seçimi temsil etmek için numaralandırma türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="59202-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="59202-113">Seçeneklerin bir birleşimini temsil etmek için, numaralandırma türünü bit bayrakları olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="59202-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="59202-114">Bit bayrakları olarak numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="59202-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="59202-115">Bir numaralandırma türünün seçeneklerin bir birleşimini temsil etmesini istiyorsanız, tek bir seçimin bit alanı olması gibi bu seçimler için enum üyelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="59202-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="59202-116">Diğer bir şekilde, bu enum üyelerinin ilişkili değerleri iki gücün yetkileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59202-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="59202-117">Daha sonra, [bitwise mantıksal `|` `&` işleçleri](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kullanabilirsiniz veya sırasıyla seçenekleri veya seçenekleri kesişen kombinasyonları birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="59202-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="59202-118">Bir numaralandırma türünün bit alanlarını beyan ettiğini belirtmek için, [bayraklar](xref:System.FlagsAttribute) özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="59202-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="59202-119">Aşağıdaki örnekte de görüldüğü gibi, numaralandırma türünün tanımına bazı tipik kombinasyonlar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59202-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="59202-120">Daha fazla bilgi ve <xref:System.FlagsAttribute?displayProperty=nameWithType> örnekler için, API başvuru sayfasına ve münhasır olmayan <xref:System.Enum?displayProperty=nameWithType> üyelere ve API başvuru [sayfasının Bayraklar özniteliği](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="59202-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="59202-121">System.Enum tipi ve enum kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="59202-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="59202-122">Tür, <xref:System.Enum?displayProperty=nameWithType> tüm numaralandırma türlerinin soyut taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="59202-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="59202-123">Bir numaralandırma türü ve değerleri hakkında bilgi almak için bir dizi yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="59202-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="59202-124">Daha fazla bilgi ve <xref:System.Enum?displayProperty=nameWithType> örnekler için API başvuru sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="59202-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="59202-125">C# 7.3 ile başlayarak, bir tür parametrenin numaralandırma türü olduğunu belirtmek için taban sınıf kısıtlamasını `System.Enum` [(enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59202-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="59202-126">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="59202-126">Conversions</span></span>

<span data-ttu-id="59202-127">Herhangi bir numaralandırma türü için, numaralandırma türü ile altta yatan integral türü arasında açık dönüşümler vardır.</span><span class="sxs-lookup"><span data-stu-id="59202-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="59202-128">Bir enum değerini temel türüne [atarsanız,](../operators/type-testing-and-cast.md#cast-expression) sonuç bir enum üyesinin ilişkili integral değeridir.</span><span class="sxs-lookup"><span data-stu-id="59202-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="59202-129">Numaralandırma <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> türünün belirli ilişkili değere sahip bir enum üyesi ni içerip içermediğini belirlemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="59202-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="59202-130">Herhangi bir numaralandırma türü için, sırasıyla <xref:System.Enum?displayProperty=nameWithType> ve türünden [kutulama](../../programming-guide/types/boxing-and-unboxing.md) dönüşümleri var.</span><span class="sxs-lookup"><span data-stu-id="59202-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59202-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="59202-131">C# language specification</span></span>

<span data-ttu-id="59202-132">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="59202-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="59202-133">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="59202-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="59202-134">Enum değerleri ve işlemleri</span><span class="sxs-lookup"><span data-stu-id="59202-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="59202-135">Numaralandırma mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="59202-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="59202-136">Numaralandırma karşılaştırma operatörleri</span><span class="sxs-lookup"><span data-stu-id="59202-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="59202-137">Açık numaralandırma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="59202-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="59202-138">Örtük numaralandırma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="59202-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="59202-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59202-139">See also</span></span>

- [<span data-ttu-id="59202-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="59202-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="59202-141">Sabit listesi biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="59202-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="59202-142">Tasarım yönergeleri - Enum tasarım</span><span class="sxs-lookup"><span data-stu-id="59202-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="59202-143">Tasarım yönergeleri - Enum adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="59202-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="59202-144">anahtar deyimi</span><span class="sxs-lookup"><span data-stu-id="59202-144">switch statement</span></span>](../keywords/switch.md)

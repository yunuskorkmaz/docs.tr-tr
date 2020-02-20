---
title: Sabit listesi türleri C# -başvuru
description: Bir seçimi C# veya seçenek bileşimini temsil eden numaralandırma türleri hakkında bilgi edinin
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
ms.openlocfilehash: 4377d113a18d23c8a0f9a669e6112f1a8223cc79
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450875"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="6c9ca-103">Sabit listesi türleriC# (başvuru)</span><span class="sxs-lookup"><span data-stu-id="6c9ca-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="6c9ca-104">*Sabit listesi türü* (veya *enum türü*), temel alınan [integral sayısal](integral-numeric-types.md) türünün adlandırılmış sabitler kümesi tarafından tanımlanan bir [değer türüdür](value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9ca-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="6c9ca-105">Bir sabit listesi türü tanımlamak için `enum` anahtar sözcüğünü kullanın ve *enum üyelerinin*adlarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="6c9ca-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="6c9ca-106">Varsayılan olarak, sabit listesi üyelerinin ilişkili sabit değerleri `int`türündedir. Bunlar sıfır ile başlar ve tanım metin sırasını izleyerek bir artış artar.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="6c9ca-107">Bir numaralandırma türünün temel alınan türü olarak, diğer tüm [integral sayısal](integral-numeric-types.md) türlerini açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="6c9ca-108">Ayrıca, aşağıdaki örnekte gösterildiği gibi, ilişkili sabit değerleri açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6c9ca-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="6c9ca-109">Bir sabit listesi türünün tanımı içinde bir yöntem tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="6c9ca-110">Bir numaralandırma türüne işlevsellik eklemek için bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="6c9ca-111">Bir sabit listesi `E` türünün varsayılan değeri, karşılık gelen enum üyesi olmasa bile, ifade `(E)0`tarafından üretilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="6c9ca-112">Birbirini dışlayan bir veya seçenek birleşimi kümesinden seçim göstermek için bir numaralandırma türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="6c9ca-113">Seçeneklerin bir birleşimini göstermek için, bir numaralandırma türünü bit bayrakları olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="6c9ca-114">Bit bayrakları olarak numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="6c9ca-115">Bir sabit listesi türünün bir seçenek birleşimini göstermesini istiyorsanız, bu seçimler için, tek bir seçenek olan bir bit alanı olduğu gibi, numaralandırma üyelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="6c9ca-116">Diğer bir deyişle, bu sabit listesi üyelerinin ilişkili değerleri ikinin üsleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="6c9ca-117">Ardından, sırasıyla seçenekleri veya seçimleri birleştirmek için [bit düzeyinde mantıksal işleçler `|` veya `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="6c9ca-118">Bir numaralandırma türünün bit alanları bildirdiğini belirtmek için, [Flags](xref:System.FlagsAttribute) özniteliğini buna uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="6c9ca-119">Aşağıdaki örnekte gösterildiği gibi, bir numaralandırma türünün tanımına bazı tipik birleşimler da dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

<span data-ttu-id="6c9ca-120">Daha fazla bilgi ve örnek için, <xref:System.Enum?displayProperty=nameWithType> API başvurusu sayfasının <xref:System.FlagsAttribute?displayProperty=nameWithType> API başvurusu sayfasına ve [dışlamalı olmayan üyelere ve Flags özniteliği](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="6c9ca-121">System. Enum türü ve enum kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="6c9ca-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="6c9ca-122"><xref:System.Enum?displayProperty=nameWithType> türü, tüm numaralandırma türlerinin soyut temel sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="6c9ca-123">Bir numaralandırma türü ve değerleri hakkında bilgi almak için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="6c9ca-124">Daha fazla bilgi ve örnek için bkz. <xref:System.Enum?displayProperty=nameWithType> API başvurusu sayfası.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="6c9ca-125">7,3 ile C# başlayarak, bir tür parametresinin bir numaralandırma türü olduğunu belirtmek için temel sınıf kısıtlamasındaki `System.Enum` ( [enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="6c9ca-126">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="6c9ca-126">Conversions</span></span>

<span data-ttu-id="6c9ca-127">Herhangi bir numaralandırma türü için, sabit listesi türü ve temel alınan integral türü arasında açık dönüştürmeler vardır.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="6c9ca-128">Bir sabit listesi değerini temel alınan türüne [çevirebilirsiniz](../operators/type-testing-and-cast.md#cast-operator-) , sonuç bir numaralandırma üyesinin ilişkili integral değeridir.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

<span data-ttu-id="6c9ca-129">Bir sabit listesi türünün, ilişkili belirli değere sahip bir numaralandırma üyesi içerip içermediğini anlamak için <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="6c9ca-130">Herhangi bir sabit listesi türü için, sırasıyla <xref:System.Enum?displayProperty=nameWithType> türüne ve ' a [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md) çıkarma dönüştürmeleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6c9ca-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6c9ca-131">C# language specification</span></span>

<span data-ttu-id="6c9ca-132">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="6c9ca-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6c9ca-133">Sabit listeleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="6c9ca-134">Sabit listesi değerleri ve işlemleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="6c9ca-135">Sabit listesi mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="6c9ca-136">Sabit Listesi karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="6c9ca-137">Açık sabit listesi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="6c9ca-138">Örtük numaralandırma dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="6c9ca-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c9ca-139">See also</span></span>

- [<span data-ttu-id="6c9ca-140">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="6c9ca-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6c9ca-141">Sabit listesi biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="6c9ca-142">Tasarım yönergeleri-numaralandırma tasarımı</span><span class="sxs-lookup"><span data-stu-id="6c9ca-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="6c9ca-143">Tasarım yönergeleri-sabit listesi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="6c9ca-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="6c9ca-144">Switch deyimleri</span><span class="sxs-lookup"><span data-stu-id="6c9ca-144">switch statement</span></span>](../keywords/switch.md)

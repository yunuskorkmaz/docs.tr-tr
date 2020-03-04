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
ms.openlocfilehash: 77c7b7bd7f3e59fbe782755c829f18cf1cefc725
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239826"
---
# <a name="enumeration-types-c-reference"></a>Sabit listesi türleriC# (başvuru)

*Sabit listesi türü* (veya *enum türü*), temel alınan [integral sayısal](integral-numeric-types.md) türünün adlandırılmış sabitler kümesi tarafından tanımlanan bir [değer türüdür](value-types.md) . Bir sabit listesi türü tanımlamak için `enum` anahtar sözcüğünü kullanın ve *enum üyelerinin*adlarını belirtin:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Varsayılan olarak, sabit listesi üyelerinin ilişkili sabit değerleri `int`türündedir. Bunlar sıfır ile başlar ve tanım metin sırasını izleyerek bir artış artar. Bir numaralandırma türünün temel alınan türü olarak, diğer tüm [integral sayısal](integral-numeric-types.md) türlerini açıkça belirtebilirsiniz. Ayrıca, aşağıdaki örnekte gösterildiği gibi, ilişkili sabit değerleri açıkça belirtebilirsiniz:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Bir sabit listesi türünün tanımı içinde bir yöntem tanımlayamazsınız. Bir numaralandırma türüne işlevsellik eklemek için bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md)oluşturun.

Bir sabit listesi `E` türünün varsayılan değeri, karşılık gelen enum üyesi olmasa bile, ifade `(E)0`tarafından üretilen değerdir.

Birbirini dışlayan bir veya seçenek birleşimi kümesinden seçim göstermek için bir numaralandırma türü kullanırsınız. Seçeneklerin bir birleşimini göstermek için, bir numaralandırma türünü bit bayrakları olarak tanımlayın.

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir sabit listesi türünün bir seçenek birleşimini göstermesini istiyorsanız, bu seçimler için, tek bir seçenek olan bir bit alanı olduğu gibi, numaralandırma üyelerini tanımlayın. Diğer bir deyişle, bu sabit listesi üyelerinin ilişkili değerleri ikinin üsleri olmalıdır. Ardından, sırasıyla seçenekleri veya seçimleri birleştirmek için [bit düzeyinde mantıksal işleçler `|` veya `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kullanabilirsiniz. Bir numaralandırma türünün bit alanları bildirdiğini belirtmek için, [Flags](xref:System.FlagsAttribute) özniteliğini buna uygulayın. Aşağıdaki örnekte gösterildiği gibi, bir numaralandırma türünün tanımına bazı tipik birleşimler da dahil edebilirsiniz.

[!code-csharp[enum flags](~/samples/snippets/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

Daha fazla bilgi ve örnek için, <xref:System.Enum?displayProperty=nameWithType> API başvurusu sayfasının <xref:System.FlagsAttribute?displayProperty=nameWithType> API başvurusu sayfasına ve [dışlamalı olmayan üyelere ve Flags özniteliği](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) bölümüne bakın.

## <a name="the-systemenum-type-and-enum-constraint"></a>System. Enum türü ve enum kısıtlaması

<xref:System.Enum?displayProperty=nameWithType> türü, tüm numaralandırma türlerinin soyut temel sınıfıdır. Bir numaralandırma türü ve değerleri hakkında bilgi almak için çeşitli yöntemler sağlar. Daha fazla bilgi ve örnek için bkz. <xref:System.Enum?displayProperty=nameWithType> API başvurusu sayfası.

7,3 ile C# başlayarak, bir tür parametresinin bir numaralandırma türü olduğunu belirtmek için temel sınıf kısıtlamasındaki `System.Enum` ( [enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.

## <a name="conversions"></a>Dönüşümler

Herhangi bir numaralandırma türü için, sabit listesi türü ve temel alınan integral türü arasında açık dönüştürmeler vardır. Bir sabit listesi değerini temel alınan türüne [çevirebilirsiniz](../operators/type-testing-and-cast.md#cast-operator-) , sonuç bir numaralandırma üyesinin ilişkili integral değeridir.

[!code-csharp[enum conversions](~/samples/snippets/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

Bir sabit listesi türünün, ilişkili belirli değere sahip bir numaralandırma üyesi içerip içermediğini anlamak için <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> yöntemini kullanın.

Herhangi bir sabit listesi türü için, sırasıyla <xref:System.Enum?displayProperty=nameWithType> türüne ve ' a [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md) çıkarma dönüştürmeleri mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sabit listeleri](~/_csharplang/spec/enums.md)
- [Sabit listesi değerleri ve işlemleri](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Sabit listesi mantıksal işleçleri](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Sabit Listesi karşılaştırma işleçleri](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Açık sabit listesi dönüştürmeleri](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Örtük numaralandırma dönüştürmeleri](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Sabit listesi biçim dizeleri](../../../standard/base-types/enumeration-format-strings.md)
- [Tasarım yönergeleri-numaralandırma tasarımı](../../../standard/design-guidelines/enum.md)
- [Tasarım yönergeleri-sabit listesi adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [Switch deyimleri](../keywords/switch.md)

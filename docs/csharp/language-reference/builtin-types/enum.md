---
title: Sabit listesi türleri-C# başvurusu
description: Bir seçimi veya seçenek bileşimini temsil eden C# numaralandırma türleri hakkında bilgi edinin
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
ms.openlocfilehash: a21bdf63247dc5fec95922de017e1d3502e08565
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599440"
---
# <a name="enumeration-types-c-reference"></a>Numaralandırma türleri (C# Başvurusu)

*Sabit listesi türü* (veya *enum türü*), temel alınan [integral sayısal](integral-numeric-types.md) türünün adlandırılmış sabitler kümesi tarafından tanımlanan bir [değer türüdür](value-types.md) . Bir sabit listesi türü tanımlamak için `enum` anahtar sözcüğünü kullanın ve *enum üyelerinin* adlarını belirtin:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Varsayılan olarak, sabit listesi üyelerinin ilişkili sabit değerleri türündedir `int` ; sıfır ile başlar ve tanım metin sırasını izleyerek bir artış artar. Bir numaralandırma türünün temel alınan türü olarak, diğer tüm [integral sayısal](integral-numeric-types.md) türlerini açıkça belirtebilirsiniz. Ayrıca, aşağıdaki örnekte gösterildiği gibi, ilişkili sabit değerleri açıkça belirtebilirsiniz:

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

Sabit listesi türünün varsayılan değeri, `E` `(E)0` karşılık gelen enum üyesi olmasa bile, ifade tarafından üretilen değerdir.

Birbirini dışlayan bir veya seçenek birleşimi kümesinden seçim göstermek için bir numaralandırma türü kullanırsınız. Seçeneklerin bir birleşimini göstermek için, bir numaralandırma türünü bit bayrakları olarak tanımlayın.

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir sabit listesi türünün bir seçenek birleşimini göstermesini istiyorsanız, bu seçimler için, tek bir seçenek olan bir bit alanı olduğu gibi, numaralandırma üyelerini tanımlayın. Diğer bir deyişle, bu sabit listesi üyelerinin ilişkili değerleri ikinin üsleri olmalıdır. Ardından, sırasıyla [bit düzeyinde mantıksal işleçleri kullanabilir `|` veya `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) seçimler ya da seçeneklerin kesiştirelerini birleştirmek için ' i kullanabilirsiniz. Bir numaralandırma türünün bit alanları bildirdiğini belirtmek için, [Flags](xref:System.FlagsAttribute) özniteliğini buna uygulayın. Aşağıdaki örnekte gösterildiği gibi, bir numaralandırma türünün tanımına bazı tipik birleşimler da dahil edebilirsiniz.

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

Daha fazla bilgi ve örnek için API başvurusu sayfasının <xref:System.FlagsAttribute?displayProperty=nameWithType> ve [dışlamalı olmayan üyelere ve Flags özniteliği](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) bölümüne bakın <xref:System.Enum?displayProperty=nameWithType> .

## <a name="the-systemenum-type-and-enum-constraint"></a>System. Enum türü ve enum kısıtlaması

<xref:System.Enum?displayProperty=nameWithType>Tür, tüm numaralandırma türlerinin soyut temel sınıfıdır. Bir numaralandırma türü ve değerleri hakkında bilgi almak için çeşitli yöntemler sağlar. Daha fazla bilgi ve örnek için bkz <xref:System.Enum?displayProperty=nameWithType> . API başvuru sayfası.

C# 7,3 ' den başlayarak, bir `System.Enum` tür parametresinin bir numaralandırma türü olduğunu belirtmek için bir temel sınıf kısıtlamasında ( [enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz. Herhangi bir numaralandırma türü ayrıca `struct` , bir tür parametresinin null yapılamayan bir değer türü olduğunu belirtmek için kullanılan kısıtlamayı da karşılar.

## <a name="conversions"></a>Dönüşümler

Herhangi bir numaralandırma türü için, sabit listesi türü ve temel alınan integral türü arasında açık dönüştürmeler vardır. Bir sabit listesi değerini temel alınan türüne [çevirebilirsiniz](../operators/type-testing-and-cast.md#cast-expression) , sonuç bir numaralandırma üyesinin ilişkili integral değeridir.

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>Bir numaralandırma türünün, ilişkili belirli değere sahip bir numaralandırma üyesi içerip içermediğini anlamak için yöntemini kullanın.

Herhangi bir numaralandırma türü için sırasıyla türe ve türüne [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md) çıkarma dönüştürmeleri bulunur <xref:System.Enum?displayProperty=nameWithType> .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Numaralandırmalar](~/_csharplang/spec/enums.md)
- [Sabit listesi değerleri ve işlemleri](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Sabit listesi mantıksal işleçleri](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Sabit Listesi karşılaştırma işleçleri](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Açık sabit listesi dönüştürmeleri](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Örtük numaralandırma dönüştürmeleri](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Sabit listesi biçim dizeleri](../../../standard/base-types/enumeration-format-strings.md)
- [Tasarım yönergeleri-numaralandırma tasarımı](../../../standard/design-guidelines/enum.md)
- [Tasarım yönergeleri-sabit listesi adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [switch deyimi](../keywords/switch.md)

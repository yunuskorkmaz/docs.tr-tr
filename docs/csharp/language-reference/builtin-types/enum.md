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
ms.openlocfilehash: ab5eb1679f846bf0e25d90a4d0e0a71f0bdb0096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847721"
---
# <a name="enumeration-types-c-reference"></a>Numaralandırma türleri (C# referansı)

Numaralandırma *türü* (veya *enum türü),* alttaki [integral sayısal](integral-numeric-types.md) türünün adlandırılmış sabitler kümesi tarafından tanımlanan bir [değer türüdür.](value-types.md) Numaralandırma türünü tanımlamak için, anahtar `enum` kelimeyi kullanın ve *enum üyelerinin*adlarını belirtin:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Varsayılan olarak, enum üyelerinin ilişkili sabit `int`değerleri tür; sıfırla başlarlar ve tanım metin sırasını takiben bir oranında artarlar. Başka bir [integral sayısal](integral-numeric-types.md) türü, bir numaralandırma türünün altında yatan bir tür olarak açıkça belirtebilirsiniz. Aşağıdaki örnekte görüldüğü gibi, ilişkili sabit değerleri de açıkça belirtebilirsiniz:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Numaralandırma türü tanımı içinde bir yöntem tanımlayamazsınız. Numaralandırma türüne işlevsellik eklemek için bir [uzantı yöntemi](../../programming-guide/classes-and-structs/extension-methods.md)oluşturun.

Numaralandırma türünün `E` varsayılan değeri, sıfır karşılık gelen `(E)0`enum üyesi olmasa bile ifade tarafından üretilen değerdir.

Birbirini dışlayan değerler kümesinden veya seçeneklerin birleşiminden bir seçimi temsil etmek için numaralandırma türü kullanırsınız. Seçeneklerin bir birleşimini temsil etmek için, numaralandırma türünü bit bayrakları olarak tanımlayın.

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir numaralandırma türünün seçeneklerin bir birleşimini temsil etmesini istiyorsanız, tek bir seçimin bit alanı olması gibi bu seçimler için enum üyelerini tanımlayın. Diğer bir şekilde, bu enum üyelerinin ilişkili değerleri iki gücün yetkileri olmalıdır. Daha sonra, [bitwise mantıksal `|` `&` işleçleri](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kullanabilirsiniz veya sırasıyla seçenekleri veya seçenekleri kesişen kombinasyonları birleştirmek için. Bir numaralandırma türünün bit alanlarını beyan ettiğini belirtmek için, [bayraklar](xref:System.FlagsAttribute) özniteliğini uygulayın. Aşağıdaki örnekte de görüldüğü gibi, numaralandırma türünün tanımına bazı tipik kombinasyonlar da ekleyebilirsiniz.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Daha fazla bilgi ve <xref:System.FlagsAttribute?displayProperty=nameWithType> örnekler için, API başvuru sayfasına ve münhasır olmayan <xref:System.Enum?displayProperty=nameWithType> üyelere ve API başvuru [sayfasının Bayraklar özniteliği](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) bölümüne bakın.

## <a name="the-systemenum-type-and-enum-constraint"></a>System.Enum tipi ve enum kısıtlaması

Tür, <xref:System.Enum?displayProperty=nameWithType> tüm numaralandırma türlerinin soyut taban sınıfıdır. Bir numaralandırma türü ve değerleri hakkında bilgi almak için bir dizi yöntem sağlar. Daha fazla bilgi ve <xref:System.Enum?displayProperty=nameWithType> örnekler için API başvuru sayfasına bakın.

C# 7.3 ile başlayarak, bir tür parametrenin numaralandırma türü olduğunu belirtmek için taban sınıf kısıtlamasını `System.Enum` [(enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.

## <a name="conversions"></a>Dönüşümler

Herhangi bir numaralandırma türü için, numaralandırma türü ile altta yatan integral türü arasında açık dönüşümler vardır. Bir enum değerini temel türüne [atarsanız,](../operators/type-testing-and-cast.md#cast-operator-) sonuç bir enum üyesinin ilişkili integral değeridir.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Numaralandırma <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> türünün belirli ilişkili değere sahip bir enum üyesi ni içerip içermediğini belirlemek için yöntemi kullanın.

Herhangi bir numaralandırma türü için, sırasıyla <xref:System.Enum?displayProperty=nameWithType> ve türünden [kutulama](../../programming-guide/types/boxing-and-unboxing.md) dönüşümleri var.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Numaralandırmalar](~/_csharplang/spec/enums.md)
- [Enum değerleri ve işlemleri](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Numaralandırma mantıksal işleçleri](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Numaralandırma karşılaştırma operatörleri](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Açık numaralandırma dönüşümleri](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Örtük numaralandırma dönüşümleri](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Numaralandırma biçimi dizeleri](../../../standard/base-types/enumeration-format-strings.md)
- [Tasarım yönergeleri - Enum tasarım](../../../standard/design-guidelines/enum.md)
- [Tasarım yönergeleri - Enum adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [anahtar deyimi](../keywords/switch.md)

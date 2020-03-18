---
title: özel anahtar kelime - C# Reference
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715193"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)

Anahtar `private` kelime bir üye erişim değiştiricidir.

> Bu sayfa `private` erişimi kapsar. Anahtar `private` kelime de erişim [`private protected`](./private-protected.md) değiştiricinin bir parçasıdır.

Özel erişim en az izin verilen erişim düzeyidir. Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesi nde veya beyan edildikleri yapı içinde erişilebilir:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Aynı gövdedeki iç içe geçen türler de bu özel üyelere erişebilir.

Sınıf veya beyan edildiği yapı dışında özel bir üyeye başvurmak için bir derleme zamanı hatasıdır.

Diğer erişim `private` değiştiriciler ile karşılaştırma [için, Erişilebilirlik Düzeyleri](accessibility-levels.md) ve [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.

## <a name="example"></a>Örnek

Bu örnekte, `Employee` sınıf iki özel `name` veri `salary`üyesi içerir ve . Özel üyeler olarak, üye yöntemleri dışında erişilemezler. Özel üyelere kontrollü erişim sağlamak için adlandırılmış `GetName` ve `Salary` eklenen genel yöntemler. Üyeye `name` genel bir yöntemle erişilir ve `salary` üyeye herkese açık salt okunur bir özellik ile erişilir. (Daha fazla bilgi için [Özellikler'e](../../programming-guide/classes-and-structs/properties.md) bakın.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [Kamu](public.md)
- [protected](protected.md)
- [Iç](internal.md)

---
title: private anahtar sözcüğü C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715193"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)

`private` anahtar sözcüğü bir üye erişim değiştiricisidir.

> Bu sayfa `private` erişimi içerir. `private` anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır.

Özel erişim en az izin veren erişim düzeyidir. Özel üyelere, bu örnekte olduğu gibi, yalnızca sınıfın gövdesinde veya bildirildiği yapı içinde erişilebilir:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Aynı gövdedeki iç içe türler Ayrıca bu özel üyelere de erişebilir.

Bu, sınıf veya bildirildiği yapı dışında özel bir üyeye başvuruda bulunmak için derleme zamanı hatasıdır.

Diğer erişim değiştiricilerine sahip `private` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Örnek

Bu örnekte, `Employee` sınıfı iki özel veri üyesi içerir, `name` ve `salary`. Özel Üyeler olarak, üye yöntemleri dışında erişilemez. `GetName` ve `Salary` adlı ortak Yöntemler, Özel üyelere denetimli erişime izin verecek şekilde eklenir. `name` üyesine ortak bir yöntem yoluyla erişilir ve `salary` üyesine ortak bir salt okunurdur özelliği tarafından erişilir. (Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)

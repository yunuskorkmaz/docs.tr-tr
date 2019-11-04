---
title: private anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 19e2925cd65cc9c68ff50d370398a4f401275940
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422598"
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

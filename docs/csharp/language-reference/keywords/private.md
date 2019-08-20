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
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602015"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)

`private` Anahtar sözcüğü bir üye erişim değiştiricisidir.

> Bu sayfa erişimi `private` içerir. Anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır. `private`

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

Diğer erişim değiştiricilerine `private` kıyasla, bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Örnek

Bu örnekte, `Employee` sınıfı iki özel veri `name` üyesi içerir ve `salary`. Özel Üyeler olarak, üye yöntemleri dışında erişilemez. `GetName` Ve`Salary` adlı ortak Yöntemler, Özel üyelere denetimli erişime izin verecek şekilde eklenir. Üyeye ortak bir yöntem tarafından erişilir `salary` ve üyeye ortak bir salt okunurdur özelliği tarafından erişilir. `name` (Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)

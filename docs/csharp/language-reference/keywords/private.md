---
description: private anahtar sözcüğü-C# başvurusu
title: private anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139404"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)

`private`Anahtar sözcüğü bir üye erişim değiştiricisidir.

> Bu sayfa `private` erişimi içerir. `private`Anahtar sözcüğü ayrıca [`private protected`](./private-protected.md) erişim değiştiricisinin bir parçasıdır.

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

`private`Diğer erişim değiştiricilerine kıyasla, bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Örnek

Bu örnekte, `Employee` sınıfı iki özel veri üyesi içerir `name` ve `salary` . Özel Üyeler olarak, üye yöntemleri dışında erişilemez. Ve adlı ortak `GetName` Yöntemler `Salary` , Özel üyelere denetimli erişime izin verecek şekilde eklenir. `name`Üyeye ortak bir yöntem tarafından erişilir ve `salary` üyeye ortak bir salt okunurdur özelliği tarafından erişilir. (Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [genel](public.md)
- [protected](protected.md)
- [internal](internal.md)

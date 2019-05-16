---
title: private anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 67b2621d382651abc27cee2eadad91a6253895c1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633336"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)

`private` Anahtar sözcüğü, bir üye erişim değiştiricisi.

> Bu sayfa kapsayan `private` erişim. `private` Anahtar sözcüğü, ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.

Özel erişim en katı erişim düzeyidir. Özel üyeler, yalnızca sınıf veya yapı içinde bu örnekte olduğu gibi bildirildikleri gövdesi içinde erişilebilir:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.

Bu sınıf veya yapı birimi içinde bildirildiği dışındaki özel üye başvurmak için bir derleme zamanı hatasıdır.

Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Örnek

Bu örnekte, `Employee` sınıfı içeren iki özel veri üyeleri, `name` ve `salary`. Özel üyeler bunlar dışında üye yöntemleri tarafından erişilemez. Genel yöntemler adlı `GetName` ve `Salary` özel üyeler denetimli erişim izni vermek için eklenir. `name` Genel bir yöntem aracılığıyla erişilen üyenin ve `salary` genel bir salt okunur özelliği yoluyla erişilen üyenin. (Bkz [özellikleri](../../programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [erişilebilirlik bildirilen](~/_csharplang/spec/basic-concepts.md#declared-accessibility) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)

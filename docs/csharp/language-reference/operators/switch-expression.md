---
title: anahtar ifadesi-C# başvurusu
description: Model eşleştirme ve diğer veri iç denetim için C# anahtar ifadesini nasıl kullanacağınızı öğrenin
ms.date: 01/14/2021
ms.openlocfilehash: 55fef8d351b178fd0ec23847e81e6c56eb1367b0
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536092"
---
# <a name="switch-expression-c-reference"></a>switch ifadesi (C# Başvurusu)

Bu makalede `switch` C# 8,0 ' de tanıtılan ifade ele alınmaktadır. Deyimi hakkında daha fazla bilgi için `switch` , [deyimler](../keywords/index.md) bölümünde bulunan [ `switch` deyimindeki](../keywords/switch.md) makaleye bakın.

## <a name="basic-example"></a>Temel örnek

`switch`İfade `switch` bir ifade bağlamında for-LIKE semantiğini sağlar. Anahtar kolları bir değer üretmediğinde kısa bir sözdizimi sağlar. Aşağıdaki örnek, bir anahtar ifadesinin yapısını gösterir. `enum`Bir çevrimiçi haritadaki bir temsil eden görsel yönden karşılık gelen değerleri karşılık gelen Kardinal yöne çevirir:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

Yukarıdaki örnek, bir anahtar ifadesinin temel öğelerini gösterir:

- *Aralık ifadesi*: önceki örnek değişkeni `direction` Aralık ifadesi olarak kullanır.
- *Anahtar ifadesi kolları*: her anahtar ifadesi ARM bir *model*, isteğe bağlı bir *Case Guard*, `=>` belirteç ve bir *ifade* içerir.

*Switch ifadesinin* sonucu, *stili* *Aralık ifadesiyle* eşleşen ve *Case Guard* varsa, olarak değerlendirilen ilk *anahtar ifadesi ARM* ifadesinin değeridir `true` . Belirtecin sağ tarafındaki *ifade* `=>` bir ifade deyimi olamaz.

*Anahtar ifadesi kolları* metin sırasıyla değerlendirilir. Daha yüksek bir anahtar *ifadesi ARM* , tüm değerleriyle eşleştiğinden, derleyici bir alt *anahtar ifadesi ARM* seçilemez bir hata verir.

## <a name="patterns-and-case-guards"></a>Desenler ve durum koruyucuları

Birçok desen anahtar ifadesi kolları içinde desteklenir. Önceki örnek *sabit bir model* kullanır. *Sabit bir düzende* Aralık ifadesi bir değer ile karşılaştırılır. Bu değer, bir derleme zamanı sabiti olmalıdır. *Tür stili* , Aralık ifadesini bilinen bir türle karşılaştırır. Aşağıdaki örnek, bir dizideki üçüncü öğeyi alır. Sıranın türüne göre farklı yöntemler kullanır:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

Desenler yinelemeli olabilir, burada bir desen bir türü sınar ve bu tür eşleşiyorsa, desen Aralık ifadesinde bir veya daha fazla özellik değerleriyle eşleşir. Önceki örneği genişletmek için özyinelemeli desenleri kullanabilirsiniz. 3 ' ten az öğeye sahip diziler için anahtar ifadesi kolları eklersiniz. Özyinelemeli desenler aşağıdaki örnekte gösterilmiştir:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Özyinelemeli desenler, Aralık ifadesinin özelliklerini inceleyebilir, ancak rastgele kod yürütüelenemez.  `when` Diğer dizi türlerine benzer denetimler sağlamak için, yan tümcesinde belirtilen bir Case Guard kullanabilirsiniz:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

Son olarak, `_` `null` başka bir anahtar ifadesi ARM tarafından işlenmemiş olan catch bağımsız değişkenlerine ve düzenine ve düzenine ekleyebilirsiniz. Bu, anahtar ifadesini *ayrıntılı* hale getirir, yani Aralık ifadesinin olası bir değeri işlenir. Aşağıdaki örnek bu ifade kolları ekler:

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

Yukarıdaki örnek bir model ekler `null` ve `IEnumerable<T>` tür modelini bir `_` düzene dönüştürür. Bu `null` kalıp, anahtar ifadesi ARM olarak null denetimi sağlar. Bu ARM için ifadesi bir oluşturur <xref:System.ArgumentNullException> . `_`Bu model, önceki kollu eşleşmeyen tüm girişlerle eşleşir. Bu, denetim sonrasında gelmelidir `null` veya girişleri eşleşmelidir `null` .

## <a name="non-exhaustive-switch-expressions"></a>Ayrıntılı olmayan anahtar ifadeleri

Anahtar ifadesinin desenlerinin hiçbiri bir bağımsız değişkeni yakalarsa, çalışma zamanı bir özel durum oluşturur. .NET Core 3,0 ve sonraki sürümlerinde, özel durum bir ' dır <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType> . .NET Framework, özel durum bir olur <xref:System.InvalidOperationException> .

## <a name="see-also"></a>Ayrıca bkz.

- [Özyinelemeli desenler için C# dil belirtimi teklifi](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)
- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Desen eşleştirme](../../pattern-matching.md)

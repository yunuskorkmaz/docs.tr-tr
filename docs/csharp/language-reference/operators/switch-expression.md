---
title: anahtar ifadesi-C# başvurusu
description: Model eşleştirme ve diğer veri iç denetim için C# anahtar ifadesini nasıl kullanacağınızı öğrenin
ms.date: 03/19/2020
ms.openlocfilehash: f53cbe873c841271f64496e4e5ff1f11750c7b8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140662"
---
# <a name="switch-expression-c-reference"></a>switch ifadesi (C# Başvurusu)

Bu makalede C# 8,0 `switch` ' de tanıtılan ifade ele alınmaktadır. `switch` Deyimi hakkında daha fazla bilgi için, [deyimler](../keywords/index.md) bölümünde bulunan [ `switch` deyimindeki](../keywords/switch.md) makaleye bakın.

## <a name="basic-example"></a>Temel örnek

`switch` İfade bir ifade bağlamında `switch`for-LIKE semantiğini sağlar. Anahtar kolları bir değer üretmediğinde kısa bir sözdizimi sağlar. Aşağıdaki örnek, bir anahtar ifadesinin yapısını gösterir. Bir çevrimiçi haritadaki bir `enum` temsil eden görsel yönden karşılık gelen değerleri karşılık gelen Kardinal yöne çevirir:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

Yukarıdaki örnek, bir anahtar ifadesinin temel öğelerini gösterir:

- *Aralık ifadesi*: önceki örnek değişkeni `direction` Aralık ifadesi olarak kullanır.
- *Anahtar ifadesi kolları*: her anahtar ifadesi ARM bir *model*, isteğe bağlı bir *Case Guard*, `=>` belirteç ve bir *ifade*içerir.

*Switch ifadesinin* sonucu, *stili* *Aralık ifadesiyle* eşleşen ve *Case Guard*varsa, olarak `true`değerlendirilen ilk *anahtar ifadesi ARM* ifadesinin değeridir. Belirtecin sağ tarafındaki ifade bir ifade deyimi olamaz. *expression* `=>`

*Anahtar ifadesi kolları* metin sırasıyla değerlendirilir. Daha yüksek bir anahtar *ifadesi ARM* , tüm değerleriyle eşleştiğinden, derleyici bir alt *anahtar ifadesi ARM* seçilemez bir hata verir.

## <a name="patterns-and-case-guards"></a>Desenler ve durum koruyucuları

Birçok desen anahtar ifadesi kolları içinde desteklenir. Önceki örnek bir *değer deseninin*kullanıldığı. Bir *değer stili* , Aralık ifadesini bir değerle karşılaştırır. Bu değer bir derleme zamanı sabiti olmalıdır. *Tür stili* , Aralık ifadesini bilinen bir türle karşılaştırır. Aşağıdaki örnek, bir dizideki üçüncü öğeyi alır. Sıranın türüne göre farklı yöntemler kullanır:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Desenler yinelemeli olabilir, burada bir desen bir türü sınar ve bu tür eşleşiyorsa, desen Aralık ifadesinde bir veya daha fazla özellik değerleriyle eşleşir. Önceki örneği genişletmek için özyinelemeli desenleri kullanabilirsiniz. 3 ' ten az öğeye sahip diziler için anahtar ifadesi kolları eklersiniz. Özyinelemeli desenler aşağıdaki örnekte gösterilmiştir:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Özyinelemeli desenler, Aralık ifadesinin özelliklerini inceleyebilir, ancak rastgele kod yürütüelenemez. Diğer dizi türlerine benzer denetimler sağlamak için, `when` yan tümcesinde belirtilen bir *Case Guard*kullanabilirsiniz:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Son olarak, başka bir anahtar `_` ifadesi ARM tarafından `null` işlenmemiş olan catch bağımsız değişkenlerine ve düzenine ve düzenine ekleyebilirsiniz. Bu, anahtar ifadesini *ayrıntılı*hale getirir, yani Aralık ifadesinin olası bir değeri işlenir. Aşağıdaki örnek bu ifade kolları ekler:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

Yukarıdaki örnek bir `null` model ekler ve `IEnumerable<T>` tür modelini bir `_` düzene dönüştürür. Bu `null` kalıp, anahtar ifadesi ARM olarak null denetimi sağlar. Bu ARM için ifadesi bir <xref:System.ArgumentNullException>oluşturur. Bu `_` model, önceki kollu eşleşmeyen tüm girişlerle eşleşir. Bu, `null` denetim sonrasında gelmelidir veya girişleri eşleşmelidir `null` .

[Özyinelemeli desenler](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)Için C# Language spec teklifinde daha fazla bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Model eşleştirme](../../pattern-matching.md)

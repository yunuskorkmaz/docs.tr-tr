---
title: anahtar ifadesi - C# başvurusu
description: Desen eşleştirme ve diğer veri içgözlemleri için C# anahtarı ifadesini nasıl kullanacağınızı öğrenin
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249790"
---
# <a name="switch-expression-c-reference"></a>anahtar ifadesi (C# başvurusu)

Bu makale, `switch` C# 8.0'da tanıtılan ifadeyi kapsar. İfade yle `switch` ilgili bilgi [için, deyimler](../keywords/index.md) bölümündeki [ `switch` ifadeyle](../keywords/switch.md) ilgili makaleye bakın.

## <a name="basic-example"></a>Temel örnek

İfade, `switch` bir `switch`ifade bağlamında -benzeri anlambilimsağlar. Anahtar kolları bir değer ürettiğinde kısa bir sözdizimi sağlar. Aşağıdaki örnekte bir anahtar ifadesinin yapısı gösterilmektedir. Çevrimiçi haritada temsil `enum` eden görsel yönlerden ilgili kardinal istikametine değerleri çevirir:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

Önceki örnek, bir anahtar ifadesinin temel öğelerini gösterir:

- *Aralık ifadesi*: Önceki örnek, `direction` aralık ifadesi olarak değişkeni kullanır.
- *Anahtar ifade kolları*: Her anahtar ifade kolu bir *desen,* isteğe bağlı *bir servis talebi koruma,* `=>` belirteç ve bir *ifade*içerir.

*Anahtar ifadesinin* sonucu, *desen* *aralık ifadesiyle* eşleşen ve *neden koruma*alanı , varsa `true`, değerlenen ilk anahtar ifade *kolunun* ifadesinin değeridir. Belirteç `=>` sağdaki *ifade* bir ifade deyimi olamaz.

*Anahtar ifade kolları* metin sırasına göre değerlendirilir. Derleyici, daha yüksek bir *anahtar ifade kolu* tüm değerleriyle eşleştiğinden, daha düşük bir anahtar ifade *kolu* seçilemediği zaman bir hata verir.

## <a name="patterns-and-case-guards"></a>Desenler ve dava korumaları

Anahtar ifade kollarında birçok desen desteklenir. Önceki örnekte bir *değer deseni*kullanılmıştır. *Değer deseni,* aralık ifadesini bir değerle karşılaştırır. Bu değer derleme zaman sabiti olmalıdır. *Tür deseni,* aralık ifadesini bilinen bir türle karşılaştırır. Aşağıdaki örnek, bir diziden üçüncü öğeyi alır. Sıranın türüne göre farklı yöntemler kullanır:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Desenler özyinelemeli olabilir, burada bir desen bir türü sınar ve bu tür eşleşirse, desen aralık ifadesinde bir veya daha fazla özellik değerleriyle eşleşir. Önceki örneği genişletmek için özyinelemeli desenler kullanabilirsiniz. 3'ten az öğeye sahip diziler için geçiş ifade kolları eklersiniz. Özyinelemeli desenler aşağıdaki örnekte gösterilmiştir:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Özyinelemeli desenler aralık ifadesinin özelliklerini inceleyebilir, ancak rasgele kod yürütemez. Diğer sıra *case guard*türleri için benzer `when` denetimler sağlamak için bir yan tümcede belirtilen bir servis talebi koruması kullanabilirsiniz:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Son olarak, başka `_` bir `null` anahtar ifade kolu tarafından işlenmemiş bağımsız değişkenleri yakalamak için desen ve desen ekleyebilirsiniz. Bu, anahtar ifadesini *kapsamlı*yapar, yani aralık ifadesinin olası herhangi bir değeri işlenir. Aşağıdaki örnek, bu ifade silah ekler:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

Önceki örnek bir `null` desen ekler ve `IEnumerable<T>` tür deseni bir `_` desen değiştirir. Desen, `null` anahtar ifade kolu olarak null denetimi sağlar. Bu kol için ifade <xref:System.ArgumentNullException>bir atar . Desen, `_` önceki kollarla eşleşmemiş tüm girişler ile eşleşir. Çekten `null` sonra gelmesi gerekir, yoksa `null` girişleri eşleşir.

[Özyinelemeli desenler](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)için C# dil spec önerisi daha fazla okuyabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Desen eşleştirme](../../pattern-matching.md)

---
title: işaretlenmemiş anahtar kelime - C# Başvurusu
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713007"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)

Anahtar `unchecked` kelime, integral türü aritmetik işlemleri ve dönüşümleri için taşma denetimini bastırmak için kullanılır.

Denetlenmemiş bir bağlamda, bir ifade hedef türünün aralığıdışında bir değer üretirse, taşma işaretlenmez. Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` blok veya ifadede gerçekleştirildiği için, sonucun bir arastıcı için `int1` çok büyük olması göz ardı edilir ve -2.147.483.639 değeri atanır.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Ortam `unchecked` kaldırılırsa, bir derleme hatası oluşur. İfadenin tüm terimleri sabit olduğundan, taşma derleme zamanda algılanabilir.

Sabit olmayan terimler içeren ifadeler derleme zamanında ve çalışma zamanında varsayılan olarak işaretlenmez. [Denetlenen](checked.md) ortamı etkinleştirme hakkında bilgi olup da kontrol edilmesine bakın.

Taşma için denetleme zaman aldığından, taşma tehlikesi nin olmadığı durumlarda denetlenmemiş kodun kullanılması performansı artırabilir. Ancak, taşma olasılığı varsa, denetlenmiş bir ortam kullanılmalıdır.

## <a name="example"></a>Örnek

Bu örnek, anahtar `unchecked` kelimenin nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Checked ve Unchecked](checked-and-unchecked.md)
- [Kontrol](checked.md)

---
title: in (Genel Değiştirici) - C# Başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713481"
---
# <a name="in-generic-modifier-c-reference"></a>in (Genel Değiştirici) (C# Başvurusu)

Genel tür parametreleri `in` için, anahtar kelime tür parametresinin karşıt olduğunu belirtir. Anahtar kelimeyi `in` genel arabirimlerde ve temsilcilerde kullanabilirsiniz.

Kontravariance, genel parametre tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak tanır. Bu, karşıt arabirimleri uygulayan sınıfların örtük olarak dönüştürülmesine ve temsilci türlerinin örtülü olarak dönüştürülmesine olanak tanır. Genel tür parametrelerindeki tutarlılık ve kontravarlık başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Bir tür, genel bir arabirimde karşıtlık olarak bildirilebilir veya yalnızca yöntemin geri dönüş türünü değil, yöntemin parametrelerinin türünü tanımlıyorsa temsilci olarak bildirilebilir. `In`, `ref`, `out` ve parametreler değişmez olmalıdır, yani ne eşdeğişken ne de kontrdeğişkendir.

Karşıt tür parametresi olan bir arabirim, yöntemlerinin arabirim türü parametresi tarafından belirtilenlerden daha az türdeki bağımsız değişkenleri kabul etmesine olanak tanır. <xref:System.Collections.Generic.IComparer%601> Örneğin, arabirimde, T türü zıttır, devralıyorsa `IComparer<Person>` `IComparer<Employee>` `Employee` `Person`herhangi bir özel dönüştürme yöntemi kullanmadan türünün bir nesnesini türün nesnesine atayabilirsiniz.

Karşıt bir temsilci, aynı türden, ancak daha az türetilmiş genel tür parametresi ile başka bir temsilci atanabilir.

Daha fazla bilgi için Bkz. [Covariance ve Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Karşıt genel arabirim

Aşağıdaki örnek, karşıt genel arabirimi nasıl beyan edeceğiz, genişletecek ve uygulayacağınızı gösterir. Ayrıca, bu arabirimi uygulayan sınıflar için örtülü dönüştürmeyi nasıl kullanabileceğinizi de gösterir.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Karşıt genel temsilci

Aşağıdaki örnek, karşıt bir genel temsilcinin nasıl bildirilen, anlık olarak bildirilen ve çağırılabildiğini gösterir. Ayrıca, bir temsilci türünü dolaylı olarak nasıl dönüştürebileceğinizi de gösterir.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [çıkış](out-generic-modifier.md)
- [Covariance ve Kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Değiştiriciler](index.md)

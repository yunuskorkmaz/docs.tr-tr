---
title: ın (genel değiştirici)- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713481"
---
# <a name="in-generic-modifier-c-reference"></a>in (Genel Değiştirici) (C# Başvurusu)

Genel tür parametreleri için `in` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir. Genel arabirimlerde ve temsilcilerde `in` anahtar sözcüğünü kullanabilirsiniz.

Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar. Bu, değişken karşıtı arabirimler uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar. Genel tür parametrelerindeki Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Bir tür, genel bir arabirimde veya bir yöntemin dönüş türü değil, bir yöntemin parametrelerinin türünü tanımlıyorsa yalnızca bir veya temsilcisinde değişken karşıtı olarak bildirilemez. `In`, `ref`ve `out` parametreleri sabit olmalıdır, yani bunlar birlikte değişken veya değişken karşıtı değil.

Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır. Örneğin, <xref:System.Collections.Generic.IComparer%601> arabiriminde T yazın, `IComparer<Person>` türünün bir nesnesini `IComparer<Employee>` türünün bir nesnesine `Employee` devr`Person`alırsa herhangi bir özel dönüştürme yöntemini kullanmadan atayabilirsiniz.

Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.

Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Değişken karşıtı genel arabirim

Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir. Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Değişken karşıtı genel temsilci

Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir. Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [out](out-generic-modifier.md)
- [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Değiştiriciler](index.md)

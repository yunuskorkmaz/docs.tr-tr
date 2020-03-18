---
title: anahtar kelime (genel değiştirici) - C# Başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713283"
---
# <a name="out-generic-modifier-c-reference"></a>out (genel değiştirici) (C# Reference)

Genel tür parametreleri `out` için, anahtar kelime tür parametresinin ortak olduğunu belirtir. Anahtar kelimeyi `out` genel arabirimlerde ve temsilcilerde kullanabilirsiniz.

Covariance, genel parametre tarafından belirtilenden daha türemiş bir tür kullanmanıza olanak tanır. Bu, ortak değişken arabirimleri uygulayan sınıfların örtülü olarak dönüştürülmesine ve temsilci türlerinin örtülü olarak dönüştürülmesine olanak tanır. Tutarlılık ve kontravariance başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Eşdeğişken türü parametresi olan bir arabirim, yöntemlerinin tür parametresi tarafından belirtilenlerden daha fazla tür döndürmesini sağlar. Örneğin, .NET Framework 4'te, <xref:System.Collections.Generic.IEnumerable%601>T türü nde ortak olduğundan, özel `IEnumerable(Of String)` dönüştürme yöntemleri kullanmadan `IEnumerable(Of Object)` türün bir nesnesini türün nesnesine atayabilirsiniz.

Ortak değişken temsilcisine aynı türden, ancak daha türetilmiş genel tür parametresi olan başka bir temsilci atanabilir.

Daha fazla bilgi için Bkz. [Covariance ve Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Örnek - ortak genel arabirim

Aşağıdaki örnek, bir birlikte varyant genel arabirimi nasıl bildirecek, genişletecek ve uygulayacağınızı gösterir. Ayrıca, bir birlikte varyant arabirimi uygulayan sınıflar için örtülü dönüştürmenin nasıl kullanılacağını da gösterir.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

Genel bir arabirimde, bir tür parametresi aşağıdaki koşulları karşılarsa eş değişken olarak bildirilebilir:

- Tür parametresi yalnızca arabirim yöntemlerinin dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri türü olarak kullanılmaz.

    > [!NOTE]
    > Bu kuralın bir istisnası vardır. Bir eşvaryant arabiriminde yöntem parametresi olarak karşıt bir genel temsilciniz varsa, bu temsilci için genel tür parametresi olarak ortak değişken türünü kullanabilirsiniz. Ortak ve karşıt genel temsilciler hakkında daha fazla bilgi için, [Temsilcilerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve Action Generic Delegates için Varyans kullanma'ya](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)bakın.

- Tür parametresi arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.

## <a name="example---covariant-generic-delegate"></a>Örnek - ortak varyant genel temsilci

Aşağıdaki örnek, ortak değişken bir genel temsilcinin nasıl bildirilen, anlık olarak bildirilen ve çağırılabildiğini gösterir. Ayrıca, temsilci türlerinin nasıl dönüştürüldüğünü de gösterir.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

Genel bir temsilcide, yalnızca yöntem dönüş türü olarak kullanılırsa ve yöntem bağımsız değişkenleri için kullanılmazsa, bir tür ortak değişken olarak bildirilebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Inç](in-generic-modifier.md)
- [Değiştiriciler](index.md)

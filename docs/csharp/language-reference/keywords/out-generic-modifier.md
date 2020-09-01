---
description: out anahtar sözcüğü (genel değiştirici)-C# başvurusu
title: out anahtar sözcüğü (genel değiştirici)-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142342"
---
# <a name="out-generic-modifier-c-reference"></a>Out (genel değiştirici) (C# Başvurusu)

Genel tür parametreleri için, `out` anahtar sözcüğü tür parametresinin birlikte değişken olduğunu belirtir. `out`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.

Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar. Bu, covaryant arabirimlerini uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar. Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar. Örneğin, içinde .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601> T türü de birlikte değişken ise, `IEnumerable(Of String)` herhangi bir özel dönüştürme yöntemi kullanmadan türdeki bir nesneye türünün bir nesnesine atayabilirsiniz `IEnumerable(Of Object)` .

Birlikte değişken temsilcisine aynı türde başka bir temsilci atanabilir, ancak daha türetilmiş bir genel tür parametresi olabilir.

Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Örnek-birlikte değişken genel arabirimi

Aşağıdaki örnek, bir covaryant genel arabiriminin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir. Ayrıca, birlikte değişken arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanacağınızı gösterir.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

Bir genel arabirimde, bir tür parametresi aşağıdaki koşullara uygunsa birlikte değişken olarak bildirilemez:

- Tür parametresi yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.

    > [!NOTE]
    > Bu kural için bir özel durum var. Bir covaryant arayüzünde bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, bu temsilci için ortak tür parametresi olarak covaryant türü ' ni kullanabilirsiniz. Covaryant ve değişken karşıtı genel Temsilciler hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Tür parametresi, arabirim yöntemleri için genel kısıtlama olarak kullanılmaz.

## <a name="example---covariant-generic-delegate"></a>Örnek-birlikte değişken genel temsilcisi

Aşağıdaki örnek, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir. Ayrıca, temsilci türlerini örtük olarak nasıl dönüştürebileceğiniz gösterilmektedir.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

Genel bir temsilcisinde, bir tür yalnızca bir yöntem dönüş türü olarak kullanılıyorsa ve Yöntem bağımsız değişkenleri için kullanılmazsa, birlikte değişken olarak bildirilemez.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- ['ndaki](in-generic-modifier.md)
- [Değiştiriciler](index.md)

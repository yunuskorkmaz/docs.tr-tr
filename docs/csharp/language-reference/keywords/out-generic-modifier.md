---
title: out anahtar sözcüğü (genel değiştirici) C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 121faf46f1c5ba50f132dc180e9d4f802ac91696
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422655"
---
# <a name="out-generic-modifier-c-reference"></a>Out (genel değiştirici) (C# başvuru)

Genel tür parametreleri için `out` anahtar sözcüğü, tür parametresinin birlikte değişken olduğunu belirtir. Genel arabirimlerde ve temsilcilerde `out` anahtar sözcüğünü kullanabilirsiniz.

Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar. Bu, covaryant arabirimlerini uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar. Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar. Örneğin, .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601>' de T yazın ve bir özel dönüştürme yöntemi kullanmadan `IEnumerable(Of String)` türünün bir nesnesini `IEnumerable(Of Object)` türünün bir nesnesine atayabilirsiniz.

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
- [in](in-generic-modifier.md)
- [Değiştiriciler](index.md)

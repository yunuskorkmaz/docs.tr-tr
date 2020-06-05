---
title: Out (Genel Değiştirici)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 28ae7d6fd51170aa822072fc2f5357443f51a353
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392099"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (Genel Değiştirici) (Visual Basic)

Genel tür parametreleri için `Out` anahtar sözcüğü, türün birlikte değişken olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar

Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar. Bu, değişken arabirimleri uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.

Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Kurallar

`Out`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.

Bir genel arabirimde, bir tür parametresi aşağıdaki koşullara uygunsa birlikte değişken olarak bildirilemez:

- Tür parametresi yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.

    > [!NOTE]
    > Bu kural için bir özel durum var. Bir covaryant arayüzünde bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, bu temsilci için ortak tür parametresi olarak covaryant türü ' ni kullanabilirsiniz. Covaryant ve değişken karşıtı genel Temsilciler hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Tür parametresi, arabirim yöntemleri için genel kısıtlama olarak kullanılmaz.

Genel bir temsilcisinde, bir tür parametresi yalnızca yöntem dönüş türü olarak kullanılırsa ve Yöntem bağımsız değişkenleri için kullanılmazsa birlikte değişken olarak bildirilemez.

Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.

Visual Basic, temsilci türünü belirtmeden birlikte değişken arabirimlerde olayları bildiremezsiniz. Ayrıca, birlikte değişken arabirimlerin iç içe sınıfları, numaralandırmalar veya yapıları olamaz, ancak iç içe arabirimler olabilir.

## <a name="behavior"></a>Davranış

Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar. Örneğin, içinde .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601> T türü de birlikte değişken ise, `IEnumerable(Of String)` herhangi bir özel dönüştürme yöntemi kullanmadan türdeki bir nesneye türünün bir nesnesine atayabilirsiniz `IEnumerable(Of Object)` .

Birlikte değişken temsilcisine aynı türde başka bir temsilci atanabilir, ancak daha türetilmiş bir genel tür parametresi olabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir covaryant genel arabiriminin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir. Ayrıca, birlikte değişken arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanacağınızı gösterir.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir. Ayrıca, temsilci türleri için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [İçinde](in-generic-modifier.md)

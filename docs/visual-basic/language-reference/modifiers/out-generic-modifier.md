---
title: Out (Genel Değiştirici) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: fa14e83af16cd30a72ca1c165596fa9320842fce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379230"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (Genel Değiştirici) (Visual Basic)

Genel tür parametreleri için `Out` anahtar sözcük türü birlikte değişken olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar

Kovaryans genel parametre olarak belirtilenden daha türetilmiş bir tür belirtmenize olanak sağlar. Bu değişken arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar.

Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Kurallar

Kullanabileceğiniz `Out` genel arabirimlerde ve temsilcilerde anahtar sözcük.

Genel arabiriminin tür parametresi aşağıdaki koşulları karşılıyorsa, birlikte değişken bildirilebilir:

- Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz.

    > [!NOTE]
    > Bu kuralın tek istisnası yoktur. Birlikte değişen bir arabirimde bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, birlikte değişken türünde genel tür parametre olarak bu metot temsilcisi için kullanabilirsiniz. Birlikte değişken hakkında daha fazla bilgi ve değişken karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Tür parametresi, arabirim yöntemleri için genel bir kısıtlama kullanılmaz.

Yalnızca bir yöntem dönüş türü kullanılan ve kullanılmayan yöntem bağımsız değişkenleri için genel bir temsilci, bir tür parametresi birlikte değişken olarak bildirilebilir.

Kovaryans ve kontravaryans başvuru türleri için desteklenir ancak değer türleri için desteklenmiyor.

Visual Basic'te, temsilci türü belirtmeden birlikte değişken Arabirimlerdeki olaylar bildiremezsiniz. Ayrıca, birlikte değişken arabirimleri sınıflar, numaralandırmalar ve yapılar iç içe geçmiş olamaz, ancak bunlar arabirimleri içe.

## <a name="behavior"></a>Davranış

Dönüş türü parametresi tarafından belirtilenlerden daha türetilmiş türleri metotlarını bir birlikte değişen türde parametresi olan bir arabirim sağlar. Örneğin, çünkü .NET Framework 4 içinde <xref:System.Collections.Generic.IEnumerable%601>T türü birlikte değişken, bir nesnenin atayabilirsiniz `IEnumerable(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntemini kullanmadan türü.

Birlikte değişen bir temsilci, aynı türden, ancak daha fazla türetilmiş bir genel tür parametresi ile başka bir temsilci atanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bildirmek, genişletin ve bir değişken genel arabirim uygulamak gösterilmektedir. Ayrıca, birlikte değişen bir arabirimi uygulayan sınıflar için örtük dönüştürme kullanmayı gösterir.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bildirme, oluşturma ve birlikte değişken temsilci çağırma gösterilmektedir. Ayrıca, temsilci türleri için örtük dönüştürme nasıl kullanabileceğinizi gösterir.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)

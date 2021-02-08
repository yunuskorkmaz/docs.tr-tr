---
description: 'Hakkında daha fazla bilgi edinin: ın (genel değiştirici) (Visual Basic)'
title: In (genel değiştirici)-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: e6ac95a77253b28e45a4be8a29623bdd76a231f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774544"
---
# <a name="in-generic-modifier-visual-basic"></a>In (Genel Değiştirici) (Visual Basic)

Genel tür parametreleri için, `In` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar

Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar. Bu, değişken arabirimleri uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.

Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Kurallar

`In`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.
  
Bir tür parametresi, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılırsa ve yöntem dönüş türü olarak kullanılmazsa genel bir arabirimde veya temsilcisinde değişken karşıtı olarak bildirilemez. `ByRef` parametreler birlikte değişken veya değişken karşıtı olamaz.

Kovaryans ve değişken Varyans, başvuru türleri için desteklenir ve değer türleri için desteklenmez.

Visual Basic, temsilci türünü belirtmeden olayları değişken olmayan arabirimlerde bildiremezsiniz. Ayrıca, değişken karşıtı arabirimlerde iç içe sınıflar, numaralandırmalar veya yapılar bulunamaz, ancak iç içe arabirimler olabilir.

## <a name="behavior"></a>Davranış

Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır. Örneğin, .NET Framework 4 ' te, <xref:System.Collections.Generic.IComparer%601> arabiriminde, T türü değişken değişken ise, ' `IComparer(Of Person)` `IComparer(Of Employee)` den devralırsa herhangi bir özel dönüştürme yöntemini kullanmadan, türün bir nesnesine türünün bir nesnesine atayabilirsiniz `Employee` `Person` .

Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.

## <a name="example---contravariant-generic-interface"></a>Örnek değişken karşıtı genel arabirim

Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir. Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a>Örnek değişken karşıtı genel temsilci

Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir. Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Dışı](out-generic-modifier.md)

---
title: In (Genel Değiştirici) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 91a0b9c1188820f8fc466ce1bb123b704fcd94b7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972525"
---
# <a name="in-generic-modifier-visual-basic"></a>In (Genel Değiştirici) (Visual Basic)
Genel tür parametreleri için `In` anahtar sözcüğü, tür parametresi değişken karşıtı olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kontravaryans, genel parametre olarak belirtilenden daha az türetilmiş bir tür belirtmenize olanak sağlar. Bu değişken arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar.  
  
 Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Kurallar  
 Kullanabileceğiniz `In` genel arabirimlerde ve temsilcilerde anahtar sözcük.  
  
 Yalnızca bir yöntem bağımsız kullanılan türü ise ve bir yöntemin dönüş türü olarak kullanılmayan bir tür parametresi değişken karşıtı genel arabirim veya temsilci olarak bildirilebilir. `ByRef` parametreleri olamaz birlikte değişken veya değişken karşıtı.  
  
 Kovaryans ve kontravaryans başvuru türleri için desteklenir ve değer türleri için desteklenmiyor.  
  
 Visual Basic'te, temsilci türü belirtmeden değişken karşıtı Arabirimlerdeki olaylar bildiremezsiniz. Ayrıca, değişken karşıtı arabirimleri sınıflar, numaralandırmalar ve yapılar iç içe geçmiş olamaz, ancak bunlar arabirimleri içe.  
  
## <a name="behavior"></a>Davranış  
 Yöntemlerinden daha az türetilmiş türler arabirim türü parametresi ile belirtilen değerinden bağımsız değişkenleri kabul etmek bir değişken karşıtı tür parametresine sahip bir arabirim sağlar. Örneğin, çünkü .NET Framework 4'te, <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü değişken karşıtı olduğundan, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` özel dönüştürme yöntemleri kullanılarak olmadan türü `Person` devralır `Employee`.  
  
 Başka bir temsilci aynı türden, ancak daha az türetilmiş bir genel tür parametresi değişken karşıtı temsilci atanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirmek, genişletin ve değişken karşıtı genel bir arabirim uygulamak gösterilmektedir. Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürme nasıl kullanabileceğinizi gösterir.  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, oluşturma ve değişken karşıtı Genel temsilci çağırma gösterilmektedir. Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Çıkış](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

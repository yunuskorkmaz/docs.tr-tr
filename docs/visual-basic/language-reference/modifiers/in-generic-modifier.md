---
title: "In (Genel Değiştirici) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a>In (Genel Değiştirici) (Visual Basic)
Genel tür parametreleri için `In` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar. Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.  
  
 Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Kurallar  
 Kullanabileceğiniz `In` anahtar sözcüğü genel arabirimler ve temsilciler.  
  
 Yalnızca bir tür yöntemi bağımsız değişken olarak kullanılan ve yöntemin dönüş türü olarak kullanılmayan bir tür parametresi bir genel arabirim ya da temsilci karşıtı bildirilebilir. `ByRef`parametreleri eşdeğişken olamaz veya karşıtı.  
  
 Kovaryans ve kontravaryans başvuru türleri için desteklenir ve değer türleri için desteklenmiyor.  
  
 Visual Basic'te temsilci türü belirtmeden karşıtı Arabirimlerdeki olaylar bildiremezsiniz. Ayrıca karşıtı arabirimleri sınıfları, numaralandırmaları ve yapıları işleminde içe olamaz, ancak bunlar arabirimleri.  
  
## <a name="behavior"></a>Davranış  
 Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar. Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Person` devralır `Employee`.  
  
 Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir. Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir. Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel arabirimlerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

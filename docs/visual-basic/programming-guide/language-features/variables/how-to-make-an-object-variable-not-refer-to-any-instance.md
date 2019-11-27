---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352891"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)
Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../../visual-basic/language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için  
  
- Değişkeni atama ifadesinde `Nothing` olarak ayarlayın.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kodunuz, `Nothing`olarak ayarlanmış bir nesne değişkeninin üyesine erişmeyi denediğinde, bir <xref:System.NullReferenceException> gerçekleşir. Bir nesne değişkenini sıklıkla `Nothing` olarak ayarlarsanız veya değişken başlatılamıyorsa, üye erişimlerini bir `Try...Catch...Finally` bloğuna eklemek iyi bir fikirdir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, bu nesnelerden biriyle etkin bir şekilde ilgilenirken değişkeni `Nothing` olarak ayarlayabilirsiniz. Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.NullReferenceException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

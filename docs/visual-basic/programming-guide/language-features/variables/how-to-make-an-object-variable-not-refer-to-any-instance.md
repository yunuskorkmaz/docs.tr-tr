---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004908"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)
Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../../visual-basic/language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için  
  
- Atama ifadesinde değişkeni `Nothing` olarak ayarlayın.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kodunuz `Nothing` olarak ayarlanmış bir nesne değişkeninin üyesine erişmeyi denediğinde, bir <xref:System.NullReferenceException> oluşur. @No__t-0 sıklıkla bir nesne değişkeni ayarlarsanız veya değişken başlatılmamış ise, üye erişimlerini bir `Try...Catch...Finally` bloğuna almanız iyi bir fikirdir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, bu nesnelerden biriyle etkin bir şekilde ilgilenirken değişkeni `Nothing` olarak ayarlayabilirsiniz. Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.NullReferenceException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

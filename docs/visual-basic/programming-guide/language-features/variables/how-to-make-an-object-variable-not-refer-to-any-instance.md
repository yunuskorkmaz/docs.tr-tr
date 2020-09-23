---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080261"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)

Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için  
  
- Değişkenini `Nothing` atama ifadesinde olarak ayarlayın.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kodunuz, olarak ayarlanmış bir nesne değişkeninin üyesine erişmeye çalışırsa `Nothing` , bir <xref:System.NullReferenceException> gerçekleşir. Bir nesne değişkenini sıklıkla olarak ayarlarsanız `Nothing` veya değişken başlatılmamış ise, üye erişimlerini bir blokta kapsamak iyi bir fikirdir `Try...Catch...Finally` .  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, `Nothing` bu nesnelerden biriyle etkin bir şekilde ilgilenmediği zaman değişkenini olarak ayarlayabilirsiniz. Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.NullReferenceException>
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Ataması](object-variable-assignment.md)
- [Yapma](../../../language-reference/nothing.md)
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)

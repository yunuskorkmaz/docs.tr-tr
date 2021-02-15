---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesne değişkeninin herhangi bir örneğe başvurmadığından emin olun (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 2897720b52e708847fdd139be512e578a7420241
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481876"
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
- [Nothing](../../../language-reference/nothing.md)
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)

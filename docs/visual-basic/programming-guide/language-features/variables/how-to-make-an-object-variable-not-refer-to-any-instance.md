---
title: 'Nasıl yapılır: Nesne değişken olun Başvurmamasını herhangi bir örneğine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 820d4cb9d17bf467d257bfbba5f43f07228c0b4f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663557"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Nesne değişken olun Başvurmamasını herhangi bir örneğine (Visual Basic)
Ayarı bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini kaldırmak için  
  
- Değişken kümesine `Nothing` atama deyiminin içinde.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kodunuzu bir üyesi olarak ayarlanan bir nesne değişkeninin erişmeye çalışırsa `Nothing`, <xref:System.NullReferenceException> gerçekleşir. Bir nesne değişkeninin ayarlamanız `Nothing` sık veya değişken başlatılmamış Mümkünse, kullanma, içine almanız iyi bir fikir bir `Try...Catch...Finally` blok.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Gizli veya hassas veriler içeren nesneleri için bir nesne değişkeninin kullanıyorsanız, değişkeni ayarlayabilirsiniz `Nothing` ne zaman, değil etkin bir şekilde ilgilenme nesneleri biriyle. Bu, kötü amaçlı kod verilere erişim elde etme olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.NullReferenceException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

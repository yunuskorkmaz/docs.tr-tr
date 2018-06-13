---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: bf918b762261e1dd1fc4161a10203f3d0067e454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649730"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)
Ayarlayarak bir nesne değişkeninin hiçbir nesne örneğinden ilişkisini [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Bir nesne değişkeninin hiçbir nesne örneğinden ilişkisini kaldırmak için  
  
-   Değişkeni kümesine `Nothing` atama deyimi içinde.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kodunuzu ayarlanmış olan bir nesne değişkeni üyesi erişmeye çalışırsa `Nothing`, <xref:System.NullReferenceException> oluşur. Bir nesne değişkeni ayarlarsanız `Nothing` sık veya değişkeni başlatılmadı Mümkünse, bu üye erişimleri kapsamak için iyi bir fikirdir bir `Try...Catch...Finally` bloğu.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Gizli veya hassas veri içeren nesneler için bir nesne değişkeni kullanırsanız, değişkeni ayarlayabileceğiniz `Nothing` zaman, değil etkin olarak ilgilenme Bu nesnelerden biri. Bu, kötü amaçlı kod veri erişimini olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.NullReferenceException>  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Özel durum sorunlarını giderme: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)

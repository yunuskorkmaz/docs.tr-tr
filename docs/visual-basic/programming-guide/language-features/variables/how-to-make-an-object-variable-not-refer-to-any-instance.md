---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 8f85ba0adea522851e45b20ef5024491874c9a29
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042523"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)
Ayarı bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini kaldırmak için  
  
-   Değişken kümesine `Nothing` atama deyiminin içinde.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kodunuzu bir üyesi olarak ayarlanan bir nesne değişkeninin erişmeye çalışırsa `Nothing`, <xref:System.NullReferenceException> gerçekleşir. Bir nesne değişkeninin ayarlamanız `Nothing` sık veya değişken başlatılmamış Mümkünse, kullanma, içine almanız iyi bir fikir bir `Try...Catch...Finally` blok.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Gizli veya hassas veriler içeren nesneleri için bir nesne değişkeninin kullanıyorsanız, değişkeni ayarlayabilirsiniz `Nothing` ne zaman, değil etkin bir şekilde ilgilenme nesneleri biriyle. Bu, kötü amaçlı kod verilere erişim elde etme olasılığını azaltır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.NullReferenceException>  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Özel durum sorunlarını giderme: System.NullReferenceException](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)

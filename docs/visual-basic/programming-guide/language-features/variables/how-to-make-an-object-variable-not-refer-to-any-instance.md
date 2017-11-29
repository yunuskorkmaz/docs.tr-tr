---
title: "Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişkeni ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Hiçbir şey](../../../../visual-basic/language-reference/nothing.md)  
 [Try... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Özel durum sorunlarını giderme: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)

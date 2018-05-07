---
title: Özyinelemeli Yordamlar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 8ea7741c943ea563fbd0c7649ac0ff85b2f9ebba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-procedures-visual-basic"></a>Özyinelemeli Yordamlar (Visual Basic)
A *özyinelemeli* yordam kendisini çağıran bir kullanılır. Genel olarak, Visual Basic kodu yazmak için en etkili yolu değil.  
  
 Aşağıdaki yordamda özyineleme faktöriyelini özgün bağımsız değişkeninin değerini hesaplamak için kullanılır.  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Özyinelemeli yordamlar ile ilgili önemli noktalar  
 **Koşullar sınırlama**. Özyineleme sonlandırabilir en az bir koşul için test etmek için bir özyinelemeli yordamı tasarlamanız gerekir ve bu tür bir koşul özyinelemeli çağrılara makul bir dizi içinde nerede sağlanırsa durum işlemesi gerekir. Başarısız karşılanabilir en az bir koşul olmadan yordamınız sonsuz bir döngüde yürütmenin yüksek riskli çalışır.  
  
 **Bellek kullanımı**. Uygulamanızı yerel değişkenler için alan sınırlı miktarda sahiptir. Kendisini bir yordam çağrıları her zaman bu alanı daha fazla yerel değişkenlerini ek kopyalarını kullanır. Bu işlem belirsiz bir süre devam ederse, sonunda neden olan bir <xref:System.StackOverflowException> hata.  
  
 **Verimlilik**. Özyineleme için bir döngü neredeyse her zaman değiştirebilirsiniz. Döngü ek depolama alanı başlatma ve dönüş değerleri argümanları başlatır, yükü yok. Performansınızı özyinelemeli çağrılara daha iyi olabilir.  
  
 **Karşılıklı özyineleme**. İki yordam birbirine çağırırsanız çok düşük performans ya da sonsuz bir döngüde bile, görebilirsiniz. Bu tür bir tasarım tek özyinelemeli yordamla aynı sorunları gösterir, ancak algılamak ve hata ayıklama için daha zor olabilir.  
  
 **Parantezler ile çağırma**. Zaman bir `Function` yordam çağrıları kendisini yinelemeli olarak, hiçbir bağımsız değişken listesi olsa bile parantez yordamı adıyla izlemeniz gerekir. Aksi takdirde, işlev adı geçen işlevi dönüş değerini temsil eden olarak.  
  
 **Sınama**. Bir özyinelemeli yordamı yazarsanız, çok dikkatli bazı sınırlama koşul her zaman karşıladığından emin olmak için test. Ayrıca, çok fazla özyinelemeli çağrılara olması nedeniyle bellek yetersiz çalıştıramazsınız de emin olmalısınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.StackOverflowException>  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)  
 [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Özel durum sorunlarını giderme: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)

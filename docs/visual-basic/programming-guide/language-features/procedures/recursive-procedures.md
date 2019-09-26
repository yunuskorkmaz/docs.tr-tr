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
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274351"
---
# <a name="recursive-procedures-visual-basic"></a>Özyinelemeli Yordamlar (Visual Basic)

*Özyinelemeli* yordam kendisini çağıran bir yordamdır. Genel olarak, Visual Basic kodu yazmak için en etkili yol değildir.  
  
 Aşağıdaki yordam, orijinal bağımsız değişkeninin faktöriyelini hesaplamak için özyineleme kullanır.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Özyinelemeli yordamlarla ilgili konular

 **Koşulları sınırlandırma**. Özyineleme 'yi sonlandıran en az bir koşul için test etmek üzere yinelemeli bir yordam tasarlaması gerekir ve ayrıca makul sayıda özyinelemeli çağrı içinde böyle bir koşulun karşılanmadığı durumu da işlemeniz gerekir. Başarısız olmadan karşılanabilecek en az bir koşul olmadan, yordamınız sonsuz bir döngüde yürütmenin yüksek bir riskini çalıştırır.

 **Bellek kullanımı**. Uygulamanızın yerel değişkenler için sınırlı miktarda alanı vardır. Her bir yordam kendi kendine her çağırdığında, yerel değişkenlerinin ek kopyaları için bu alanın daha fazlasını kullanır. Bu işlem süresiz olarak devam ederse, bir <xref:System.StackOverflowException> hataya neden olur.

 **Verimlilik**. Özyineleme için neredeyse her zaman bir döngü kullanabilirsiniz. Döngü, bağımsız değişken geçirme, ek depolama başlatma ve değer döndürme ek yüküne sahip değildir. Performans özyinelemeli çağrılar olmadan çok daha iyi olabilir.

 **Karşılıklı özyineleme**. İki yordam de varsa, çok kötü performans veya sonsuz bir döngü gözlemleyebilirsiniz. Böyle bir tasarım, tek bir özyinelemeli yordamla aynı sorunları sunar, ancak algılaması ve hata ayıklaması zor olabilir.

 **Parantez Ile çağırma**. Bir `Function` yordam yinelemeli olarak çağırdığında, bağımsız değişken listesi olmasa bile, parantez ile yordam adını izlemelisiniz. Aksi takdirde, işlev adı işlevin dönüş değerini temsil eden olarak alınır.

 **Test ediliyor**. Özyinelemeli bir yordam yazarsanız, her zaman sınırlandırma koşullarını karşıladığından emin olmak için bunu dikkatle sınamanız gerekir. Ayrıca çok fazla özyinelemeli çağrı olduğundan belleği tükendiğinizden emin olmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StackOverflowException>
- [Yordamlar](index.md)
- [Alt Yordamlar](sub-procedures.md)
- [İşlev Yordamları](function-procedures.md)
- [Özellik Yordamları](property-procedures.md)
- [İşleç Yordamları](operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Yordam Aşırı Yüklemesi](procedure-overloading.md)
- [Yordam Sorunlarını Giderme](troubleshooting-procedures.md)
- [Döngü Yapıları](../control-flow/loop-structures.md)

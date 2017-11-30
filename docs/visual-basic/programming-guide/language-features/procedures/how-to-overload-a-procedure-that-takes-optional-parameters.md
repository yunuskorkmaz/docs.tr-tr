---
title: "Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)
Bir veya daha fazla yordam varsa, [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri örtük aşırı hiçbiriyle aşırı yüklenmiş bir sürümünü tanımlayamazsınız. "Daha fazla bilgi için örtük aşırı yüklemeler için isteğe bağlı parametreleri" bölümüne bakın [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>İsteğe bağlı bir parametre  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>İsteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme  
  
1.  Yazma bir `Sub` veya `Function` parametre listesinde isteğe bağlı bir parametre içeren bildirimi deyimi. Kullanmayın `Optional` Bu aşırı yüklenmiş sürümünde anahtar sözcüğü.  
  
2.  Öncesinde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
3.  İsteğe bağlı bağımsız değişkeni çağıran kodu sağlar, yürütülecek yordamı kod yazın.  
  
4.  Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
5.  İsteğe bağlı parametre parametre listesinde içermez ancak bu, ilk bildirimine aynı ikinci bir bildirim deyimi yazma.  
  
6.  Çağrıyı yapan kod isteğe bağlı bağımsız değişkeni sağlamaz, yürütülecek yordamı kod yazın. Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
     Aşağıdaki örnekte iki aşırı yüklenmiş yordamlar ve son olarak geçersiz ve geçerli aşırı yüklenmiş sürümlerinin örnekleri eşdeğer bir dizi bir isteğe bağlı parametresi tanımlı bir yordam gösterir.  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>Birden çok isteğe bağlı parametreler  
 Birden fazla isteğe bağlı bir parametre ile bir yordam için normalde ikiden fazla aşırı yüklenmiş sürümlerin gerekir. Örneğin, iki isteğe bağlı parametreler vardır ve çağıran kodu sağlayın veya diğer bağımsız olarak her biri atlarsanız, dört aşırı yüklenmiş sürümlerin sağlanan bağımsız değişkenler her bir olası kombinasyonu için bir tane gerekir.  
  
 İsteğe bağlı parametrelerin sayısı arttıkça, aşırı yüklemesi karmaşıklığını artırır. N isteğe bağlı parametreler için bazı birleşimleri sağlanan bağımsız değişkenler için kabul edilebilir değil sürece 2 gereksinim ^ N aşırı sürümleri. Yordam yapısına bağlı mantığı netlik aşırı yüklenmiş tüm sürümleri tanımlamanın ek çaba hizalar bulabilirsiniz.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Birden fazla isteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme  
  
1.  Hangi sağlanan isteğe bağlı bağımsız değişkenler yordamı mantığı için kabul edilebilir birleşimleridir belirler. İsteğe bağlı bir parametre başka bağımlıysa kabul edilebilir bir birleşimi ortaya çıkabilir. Örneğin, bir parametre bir eşin adını kabul eder ve başka eşinin yaş kabul eder, yaş sağladığını ancak adı atlama bağımsız değişkenler bileşimi kabul edilebilir değil.  
  
2.  Sağlanan isteğe bağlı bağımsız değişkenler kabul edilebilir her birleşimi için yazma bir `Sub` veya `Function` karşılık gelen parametre listesi tanımlar bildirimi deyimi. Kullanmayın `Optional` anahtar sözcüğü.  
  
3.  Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
4.  Her bildirim çağrıyı yapan kod bildirim ait parametre listesine karşılık gelen bir bağımsız değişken listesi sağlar, yürütülecek yordamı kod yazın.  
  
5.  Her bir yordam ile sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [İsteğe bağlı parametreler](./optional-parameters.md)  
 [Parametre dizileri](./parameter-arrays.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Sorun giderme yordamları](./troubleshooting-procedures.md)  
 [Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)  
 [Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aşırı yükleme çözümü](./overload-resolution.md)

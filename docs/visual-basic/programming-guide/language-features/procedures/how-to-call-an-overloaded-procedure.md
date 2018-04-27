---
title: 'Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eca03de6b6dd2ca2b992196b1ae224f8fbf5068
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)
Bir yordamı aşırı yükleme avantajı çağrının esneklik olmasıdır. Çağrıyı yapan kod yordamlara geçirmek ve onu geçirerek hangi bağımsız değişkenleri olsun tek bir yordam adları çağırmak için gereken bilgileri elde edebilirsiniz.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Tanımlanan birden fazla sürümü olan bir yordam çağırma için  
  
1.  Arama kodda yordamlara geçirmek için hangi verilerin belirler.  
  
2.  Yordam çağrısı bağımsız değişken listesinde veri sunma normal bir şekilde yazın. Bağımsız değişkenler yordam için tanımlanan sürümlerinden birini parametre listesinde eşleştiğinden emin olun.  
  
3.  Hangi sürümünü çağırmak için yordamının gerekmez. Visual Basic, bağımsız değişken listesi eşleşen sürüm denetimi geçirir.  
  
     Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md). Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya bir `Integer`ve ardından her iki durumda da aynı yordamı çağırır.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı Yükleme Çözümü](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)

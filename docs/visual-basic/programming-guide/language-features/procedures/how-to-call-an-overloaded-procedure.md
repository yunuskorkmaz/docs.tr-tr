---
title: "Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff5967c1b09ad59f249297b1cf0a4ed900faf4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)
Bir yordamı aşırı yükleme avantajı çağrının esneklik olmasıdır. Çağrıyı yapan kod yordamlara geçirmek ve onu geçirerek hangi bağımsız değişkenleri olsun tek bir yordam adları çağırmak için gereken bilgileri elde edebilirsiniz.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Tanımlanan birden fazla sürümü olan bir yordam çağırma için  
  
1.  Arama kodda yordamlara geçirmek için hangi verilerin belirler.  
  
2.  Yordam çağrısı bağımsız değişken listesinde veri sunma normal bir şekilde yazın. Bağımsız değişkenler yordam için tanımlanan sürümlerinden birini parametre listesinde eşleştiğinden emin olun.  
  
3.  Hangi sürümünü çağırmak için yordamının gerekmez. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]bağımsız değişken listesi eşleşen sürüm denetimi geçirir.  
  
     Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md). Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya bir `Integer`ve ardından her iki durumda da aynı yordamı çağırır.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Sorun giderme yordamları](./troubleshooting-procedures.md)  
 [Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı yükleme çözümü](./overload-resolution.md)  
 [Aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md)

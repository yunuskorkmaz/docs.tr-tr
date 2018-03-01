---
title: "Hatalı DLL çağırma kuralı"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>Hatalı DLL çağırma kuralı
Dinamik bağlantı kitaplığı (DLL) için geçirilen bağımsız değişken tam olarak yordamı tarafından beklenen eşleşmelidir. Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası göz ile ilgilidir. Programınızı türü yanlış veya bağımsız değişken sayısı geçirilmiş bir DLL'de bir yordam çağırma.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aradığınız yordamı bildiriminde belirtilen ile tüm bağımsız değişken türleri kabul emin olun.  
  
2.  Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenler aynı sayıda geçirdiğinizden emin olun.  
  
3.  DLL yordam bağımsız değişkenleri değere göre bekler, emin olun `ByVal` yordamı için bildiriminde bu bağımsız değişkenler için belirtilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata türleri](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call deyimi](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

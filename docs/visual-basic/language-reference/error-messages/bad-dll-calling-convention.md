---
title: Hatalı DLL çağırma kuralı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-dll-calling-convention"></a>Hatalı DLL çağırma kuralı
Dinamik bağlantı kitaplığı (DLL) için geçirilen bağımsız değişken tam olarak yordamı tarafından beklenen eşleşmelidir. Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası göz ile ilgilidir. Programınızı türü yanlış veya bağımsız değişken sayısı geçirilmiş bir DLL'de bir yordam çağırma.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aradığınız yordamı bildiriminde belirtilen ile tüm bağımsız değişken türleri kabul emin olun.  
  
2.  Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenler aynı sayıda geçirdiğinizden emin olun.  
  
3.  DLL yordam bağımsız değişkenleri değere göre bekler, emin olun `ByVal` yordamı için bildiriminde bu bağımsız değişkenler için belirtilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

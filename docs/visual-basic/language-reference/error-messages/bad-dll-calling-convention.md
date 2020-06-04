---
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409887"
---
# <a name="bad-dll-calling-convention"></a>Hatalı DLL çağrı standardı
Dinamik bağlantı kitaplığına (DLL) geçirilen bağımsız değişkenler, yordam tarafından beklenen olanlarla tam olarak eşleşmelidir. Çağırma kuralları, bağımsız değişkenlerin sayısı, türü ve sırası ile ilgilenir. Programınız yanlış tür veya bağımsız değişken sayısı geçirmekte olan bir DLL 'deki bir yordamı çağırıyor olabilir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Tüm bağımsız değişken türlerinin, aradığınız yordamın bildiriminde belirtilenlerle uyumlu olduğundan emin olun.  
  
2. Aradığınız yordamın bildiriminde belirtilen sayıda bağımsız değişkeni geçirdiğinizden emin olun.  
  
3. DLL yordamı değere göre bağımsız değişkenler bekliyorsa, `ByVal` Bu yordamın bildiriminde bu bağımsız değişkenler için belirtildiğinden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../programming-guide/language-features/error-types.md)
- [Call Deyimi](../statements/call-statement.md)
- [Declare Deyimi](../statements/declare-statement.md)

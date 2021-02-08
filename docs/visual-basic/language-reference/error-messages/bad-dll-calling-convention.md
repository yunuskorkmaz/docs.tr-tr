---
description: 'Daha fazla bilgi: Hatalı DLL çağırma kuralı'
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 7e98ce5131d440a12bff4a4630da087102bdc4da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797100"
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

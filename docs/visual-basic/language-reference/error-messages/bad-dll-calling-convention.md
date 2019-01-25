---
title: Hatalı DLL çağırma kuralı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 70200b38ea3d1497daa091fa407accabaf3c4eda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715783"
---
# <a name="bad-dll-calling-convention"></a>Hatalı DLL çağırma kuralı
Bir dinamik bağlantı kitaplığı (DLL) geçirilen bağımsız değişkenler bu yordamı tarafından beklenen tam olarak eşleşmelidir. Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası ile ilgilidir. Programınızı türü yanlış veya bağımsız değişken sayısı geçirilen bir DLL içinde bir yordam çağırma.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aradığınız yordamı bildiriminde belirtilen değerlerle tüm bağımsız değişken türlerini kabul emin olun.  
  
2.  Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenleri aynı sayıda geçirdiğinizden emin olun.  
  
3.  DLL yordamı değere göre bağımsız değişken bekler, emin `ByVal` yordam bildirimi bu bağımsız değişken belirtilmiş.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

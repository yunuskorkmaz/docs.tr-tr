---
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: c4f9917a7fb807cf7da92a3bba2d3edec8045bd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813526"
---
# <a name="bad-dll-calling-convention"></a>Hatalı DLL çağrı standardı
Bir dinamik bağlantı kitaplığı (DLL) geçirilen bağımsız değişkenler bu yordamı tarafından beklenen tam olarak eşleşmelidir. Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası ile ilgilidir. Programınızı türü yanlış veya bağımsız değişken sayısı geçirilen bir DLL içinde bir yordam çağırma.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aradığınız yordamı bildiriminde belirtilen değerlerle tüm bağımsız değişken türlerini kabul emin olun.  
  
2.  Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenleri aynı sayıda geçirdiğinizden emin olun.  
  
3.  DLL yordamı değere göre bağımsız değişken bekler, emin `ByVal` yordam bildirimi bu bağımsız değişken belirtilmiş.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

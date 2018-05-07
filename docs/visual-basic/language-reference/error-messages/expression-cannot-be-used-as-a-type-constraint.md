---
title: '&#39;&lt;ifade&gt; &#39; tür sınırlaması kullanılamaz'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39;&lt;ifade&gt; &#39; tür sınırlaması kullanılamaz
Bir kısıtlama listesi bir tür parametresi geçerli bir kısıtlaması göstermiyor bir ifade içerir.  
  
 Kısıtlama listesini türü parametresine geçirilen tür bağımsız değişkeni gereksinimlerine uygular. Aşağıdaki gereksinimleri herhangi bir bileşimini belirtebilirsiniz:  
  
-   Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
-   Tür bağımsız değişkeni en fazla bir sınıftan gerekir  
  
-   Tür bağımsız değişkeni oluşturma kodu erişebilirsiniz parametresiz bir kurucusu kullanıma gerekir (dahil `New` kısıtlaması)  
  
 Kısıtlama listesinde herhangi bir belirli bir sınıf veya arabirim içermiyorsa, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:  
  
-   Tür bağımsız değişkeni bir değer türü olması gerekir (dahil `Structure` kısıtlaması)  
  
-   Tür bağımsız değişkeni bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)  
  
 Her ikisini birden belirtemezsiniz `Structure` ve `Class` aynı tür için parametre ve bunlardan birini birden çok kez belirtilemez.  
  
 **Hata Kimliği:** BC32061  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İfade ve öğeleri doğru yazdığınızdan emin olun.  
  
-   İfade önceki gereksinimlerinin listesi için uygun değilse, kısıtlama listesinden kaldırın.  
  
-   İfade bir arabirim ya da sınıf başvuruyorsa, derleyici bu arabirimi veya sınıf erişimi olduğunu doğrulayın. Projeniz için bir başvuru eklemeniz gerekebilir ve adını nitelemek gerekebilir. Daha fazla bilgi için bkz: "Projeleri başvuruları" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 

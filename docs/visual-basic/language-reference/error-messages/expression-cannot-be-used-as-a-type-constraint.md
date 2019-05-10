---
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: ff51bb27847a92b07ce6275a8ddee4789e865f08
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642799"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>'\<ifadesi >' tür kısıtlaması olarak kullanılamaz
Bir kısıtlama listesi geçerli bir tür parametresi kısıtlaması göstermiyor bir ifade içerir.  
  
 Tür parametresi için geçirilen tür bağımsız değişkeni gereksinimlerine kısıtlaması listesini uygular. Herhangi bir bileşimini aşağıdaki gereksinimleri belirtebilirsiniz:  
  
- Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
- Tür bağımsız değişkeni en fazla bir sınıftan devralmalıdır  
  
- Tür bağımsız değişkeni oluşturma kodunu erişip parametresiz bir oluşturucu kullanıma açmalıdır (dahil `New` kısıtlaması)  
  
 Kısıtlama listede herhangi bir belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilir:  
  
- Tür bağımsız değişkeni bir değer türü olmalıdır (dahil `Structure` kısıtlaması)  
  
- Tür bağımsız değişkeninin bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)  
  
 Her ikisini de belirtemezsiniz `Structure` ve `Class` aynı türünde parametre ve bunlardan birini birden çok kez belirtilemez.  
  
 **Hata Kimliği:** BC32061  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İfade ve onun öğelerine doğru yazdığınızdan emin olun.  
  
- İfade önceki gereksinimleri listesi için uymuyorsa kısıtlama listesinden kaldırın.  
  
- İfade bir arabirimin veya sınıfın başvuruyorsa, derleyici bu arabirimin veya sınıfın erişimi olduğunu doğrulayın. Adıyla nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için bkz: "Projeler için başvurular" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

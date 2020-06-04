---
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: e2ba411a5f0db21539a9cf99c7645b8c9309caab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409562"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>'\<expression>' tür kısıtlaması olarak kullanılamaz
Kısıtlama listesi, bir tür parametresinde geçerli bir kısıtlamayı temsil eden bir ifade içerir.  
  
 Bir kısıtlama listesi, tür parametresine geçirilen tür bağımsız değişkenine gereksinimleri uygular. Aşağıdaki gereksinimleri herhangi bir kombinasyonda belirtebilirsiniz:  
  
- Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
- Tür bağımsız değişkeni en çok bir sınıftan devralması gerekir  
  
- Tür bağımsız değişkeni, oluşturma kodunun erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır ( `New` kısıtlamayı dahil)  
  
 Kısıtlama listesine belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:  
  
- Tür bağımsız değişkeni bir değer türü olmalıdır ( `Structure` kısıtlamayı dahil)  
  
- Tür bağımsız değişkeni bir başvuru türü olmalıdır ( `Class` kısıtlamayı dahil)  
  
 `Structure` `Class` Aynı tür parametresi için hem hem de belirtemezsiniz ve birden çok kez belirtemezsiniz.  
  
 **Hata kimliği:** BC32061  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İfadenin ve öğelerinin doğru yazıldığından emin olun.  
  
- İfade önceki gereksinimler listesine uygun değilse, kısıtlama listesinden kaldırın.  
  
- İfade bir arabirime veya sınıfa başvuruyorsa, derleyicinin bu arabirime veya sınıfa erişimi olduğunu doğrulayın. Adını nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için, bkz. [belirtilen öğelere başvurularda](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)"projelere başvurular".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

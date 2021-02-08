---
description: "Hakkında daha fazla bilgi edinin: BC32061: ' <expression> ' tür kısıtlaması olarak kullanılamaz"
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 3484c617b28ed068c917c83454b866f8dd50c5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796411"
---
# <a name="bc32061-expression-cannot-be-used-as-a-type-constraint"></a>BC32061: ' \<expression> ' tür kısıtlaması olarak kullanılamaz

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
- [Değer türleri ve başvuru türleri](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

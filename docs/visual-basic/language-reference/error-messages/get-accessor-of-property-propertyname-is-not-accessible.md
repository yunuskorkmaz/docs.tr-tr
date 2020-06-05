---
title: "'<propertyname>' özelliğinin 'Get' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402920"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>'\<propertyname>' özelliğinin 'Get' erişimcisine erişilemiyor
Bir ifade, özelliğin yordamına erişimi olmayan bir özelliğin değerini almaya çalışır `Get` .  
  
 [Get deyiminden](../statements/get-statement.md) daha kısıtlayıcı bir erişim düzeyiyle [işaretlenmişse, özellik](../statements/property-statement.md)değerini okuma girişimi aşağıdaki durumlarda başarısız olabilir:  
  
- `Get`Ifade [Private](../modifiers/private.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıfın veya yapının dışındadır.  
  
- `Get`Ifade [korumalı](../modifiers/protected.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıf veya yapı içinde ya da türetilmiş bir sınıfta değil.  
  
- `Get`Ifade [arkadaş](../modifiers/friend.md) olarak işaretlenmiş ve çağıran kod, özelliğin tanımlandığı derlemede değil.  
  
 **Hata kimliği:** BC31103  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Özelliği tanımlayan kaynak kodun denetimine sahipseniz, `Get` yordamı özelliğin kendisiyle aynı erişim düzeyiyle bildirmeyi göz önünde bulundurun.  
  
- Özelliği tanımlayan kaynak kodu denetimine sahip değilseniz veya `Get` yordam erişim düzeyini özelliğin kendisinden daha fazla kısıtlamanız gerekiyorsa, özellik değerini okuyan ifadeyi özelliğe daha iyi erişimi olan bir kod bölgesine taşımayı deneyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../programming-guide/language-features/procedures/property-procedures.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)

---
description: "Hakkında daha fazla bilgi edinin: BC31103: ' ' özelliğinin ' Get ' erişimcisi <propertyname> erişilebilir değil"
title: "'<propertyname>' özelliğinin 'Get' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 3517bc7ec512ec99909539eb4d7cf3fafe9016fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796138"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a>BC31103: ' ' özelliğinin ' Get ' erişimcisi \<propertyname> erişilebilir değil

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

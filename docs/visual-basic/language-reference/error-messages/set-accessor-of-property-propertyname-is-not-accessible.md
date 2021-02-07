---
description: "Hakkında daha fazla bilgi edinin: BC31102: ' ' özelliğinin ' Set ' erişimcisine <propertyname> erişilemiyor"
title: "'<propertyname>' özelliğinin 'Set' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: da4d29933ca140bd9fa1a15758b64667013a8032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675084"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a>BC31102: ' ' özelliğinin ' Set ' erişimcisine \<propertyname> erişilemiyor

Bir ifade, özelliğin yordamına erişimi olmayan bir özelliğin değerini depolamaya çalışır `Set` .

 [Set deyimleri](../statements/set-statement.md) , [Property deyiminden](../statements/property-statement.md)daha kısıtlayıcı bir erişim düzeyiyle işaretlenmişse, aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:

- `Set`Ifade [Private](../modifiers/private.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıfın veya yapının dışındadır.

- `Set`Ifade [korumalı](../modifiers/protected.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıf veya yapı içinde ya da türetilmiş bir sınıfta değil.

- `Set`Ifade [arkadaş](../modifiers/friend.md) olarak işaretlenmiş ve çağıran kod, özelliğin tanımlandığı derlemede değil.

 **Hata kimliği:** BC31102

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Özelliği tanımlayan kaynak kodun denetimine sahipseniz, `Set` yordamı özelliğin kendisiyle aynı erişim düzeyiyle bildirmeyi göz önünde bulundurun.

- Özelliği tanımlayan kaynak kodu denetimine sahip değilseniz veya `Set` yordam erişim düzeyini özelliğin kendisinden daha fazla kısıtlamanız gerekiyorsa, özellik değerini ayarlayan ifadeyi özelliğe daha iyi erişimi olan bir kod bölgesine taşımayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../programming-guide/language-features/procedures/property-procedures.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)

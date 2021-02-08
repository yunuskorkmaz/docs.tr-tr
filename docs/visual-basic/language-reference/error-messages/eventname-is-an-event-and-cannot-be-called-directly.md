---
description: "Hakkında daha fazla bilgi edinin: BC32022: ' <eventname> ' bir olaydır ve doğrudan çağrılamaz"
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: f9d4b8fe54e1101e7963933f871cf5af2c1af903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796450"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022: ' \<eventname> ' bir olaydır ve doğrudan çağrılamaz

' <`eventname`> ' bir olaydır, bu nedenle doğrudan çağrılamaz. Bir `RaiseEvent` olayı yükseltmek için bir ifade kullanın.

 Yordam çağrısı, yordam adı için bir olay belirtir. Olay işleyicisi bir yordamdır, ancak olayın kendisi, oluşturulması ve işlenmesi gereken bir sinyal aygıtıdır.

 **Hata kimliği:** BC32022

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bir `RaiseEvent` olayı işaret etmek ve onu işleyen yordamı ya da yordamları çağırmak için bir ifade kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)

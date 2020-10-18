---
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161991"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022: ' \<eventname> ' bir olaydır ve doğrudan çağrılamaz

' <`eventname`> ' bir olaydır, bu nedenle doğrudan çağrılamaz. Bir `RaiseEvent` olayı yükseltmek için bir ifade kullanın.

 Yordam çağrısı, yordam adı için bir olay belirtir. Olay işleyicisi bir yordamdır, ancak olayın kendisi, oluşturulması ve işlenmesi gereken bir sinyal aygıtıdır.

 **Hata kimliği:** BC32022

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bir `RaiseEvent` olayı işaret etmek ve onu işleyen yordamı ya da yordamları çağırmak için bir ifade kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)

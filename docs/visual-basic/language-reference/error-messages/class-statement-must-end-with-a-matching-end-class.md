---
description: "Hakkında daha fazla bilgi edinin: BC30481: ' class ' ifadesinin eşleşen bir ' End Class ile bitmesi gerekir"
title: "'Class' deyimi eşleşen bir 'End Class' ile bitmelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: b0d2d89e9e3549b24f9c923e271b15b3b02026b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796788"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a>BC30481: ' class ' ifadesinin eşleşen bir ' End Class ' ile bitmesi gerekir

`Class` bir bloğu başlatmak için kullanılır `Class` ; Bu nedenle, bloğu sonlandıran eşleşen bir deyimle birlikte yalnızca bloğun başlangıcında görünebilirler `End Class` . Bir yedekli `Class` deyiminiz var veya kendi bloğundan sonlandırılamıyor `Class` `End Class` .

 **Hata kimliği:** BC30481

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Gereksiz deyimin yerini bulun ve kaldırın `Class` .

- `Class`Bloğu eşleştirme ile sonuçlandırma `End Class` .

## <a name="see-also"></a>Ayrıca bkz.

- [End \<keyword> ekstresi](../statements/end-keyword-statement.md)
- [Class Deyimi](../statements/class-statement.md)

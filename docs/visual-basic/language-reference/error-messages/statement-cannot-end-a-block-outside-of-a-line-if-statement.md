---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161341"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005: deyimin bir satır ' If ' ifadesinin dışında bir blok sonlandırılamıyor

Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` . Tek satırlı `If` deyimler `End If` deyimini kullanmaz.

 **Hata kimliği:** BC32005

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .

## <a name="see-also"></a>Ayrıca bkz.

- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)

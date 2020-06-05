---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400324"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` . Tek satırlı `If` deyimler `End If` deyimini kullanmaz.  
  
 **Hata kimliği:** BC32005  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)

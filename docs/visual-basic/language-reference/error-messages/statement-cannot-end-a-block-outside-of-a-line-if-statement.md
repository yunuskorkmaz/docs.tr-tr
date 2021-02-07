---
description: "Hakkında daha fazla bilgi edinin: BC32005: deyimin bir satır ' If ' ifadesinin dışında bir blok sonlandırılamıyor"
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: afe856b2c2ea3fa1db029d35c5b876f5d67da411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731166"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>BC32005: deyimin bir satır ' If ' ifadesinin dışında bir blok sonlandırılamıyor

Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` . Tek satırlı `If` deyimler `End If` deyimini kullanmaz.

 **Hata kimliği:** BC32005

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .

## <a name="see-also"></a>Ayrıca bkz.

- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)

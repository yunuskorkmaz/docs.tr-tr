---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593264"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
Tek satırlı `If` deyimi biri olan virgülle (:) ayırarak çeşitli deyimleri içeren bir `End` deyim için bir denetim bloğu tek satır dışında `If`. Tek satırlı `If` deyimleri kullanmayın `End If` deyimi.  
  
 **Hata Kimliği:** BC32005  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tek satırlı taşıma `If` içeren denetim bloğu dışında bir deyim `End If` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

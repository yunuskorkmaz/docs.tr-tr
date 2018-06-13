---
title: Deyimi, bir satırı dışında blok bitemez &#39;varsa&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596690"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Deyimi, bir satırı dışında blok bitemez &#39;varsa&#39; deyimi
Tek satırlı `If` deyimi içeren birkaç deyimleri biri olan iki nokta işareti (:), ayrılmış bir `End` tek satırlı dışında bir denetim bloğu bildirimi `If`. Tek satırlı `If` deyimleri kullanmayın `End If` deyimi.  
  
 **Hata Kimliği:** BC32005  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tek satırlı taşıma `If` deyimi içeren denetim bloğu dışında `End If` deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

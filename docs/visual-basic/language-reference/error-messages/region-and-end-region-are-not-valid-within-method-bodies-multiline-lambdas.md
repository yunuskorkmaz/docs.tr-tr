---
title: '&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri çok satırlı lambdalar içinde geçerli değildir'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593239"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir
`#Region` Bloğu bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir. Daraltılabilir bir bölgedeki bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.  
  
 **Hata Kimliği:** BC32025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Önceki yordam ile düzgün şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.  
  
2.  Emin `#Region` ve `#End Region` yönergeleri olan aynı kod bloğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)

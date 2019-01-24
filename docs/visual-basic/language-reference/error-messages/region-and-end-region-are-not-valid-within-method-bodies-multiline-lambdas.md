---
title: '&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri / çok satırlı lambdalar içinde geçerli değildir'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737221"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; ve &#39;#End Region&#39; deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir
`#Region` Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmesi gerekir. Daraltılabilir bir bölgeye bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.  
  
 **Hata Kimliği:** BC32025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yukarıdaki yordamı ile düzgün bir şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.  
  
2.  Emin `#Region` ve `#End Region` yönergeleridir aynı kod bloğu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)

---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri / çok satırlı lambdalar içinde geçerli değildir."
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303914"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir
`#Region` Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmesi gerekir. Daraltılabilir bir bölgeye bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.  
  
 **Hata Kimliği:** BC32025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yukarıdaki yordamı ile düzgün bir şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.  
  
2. Emin `#Region` ve `#End Region` yönergeleridir aynı kod bloğu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)

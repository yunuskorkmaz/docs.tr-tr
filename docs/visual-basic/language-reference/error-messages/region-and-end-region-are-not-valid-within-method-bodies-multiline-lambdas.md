---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: e3147b6192f54ce85d0fecd6b67f7d80f6281b54
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870884"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir

`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir. Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.  
  
 **Hata kimliği:** BC32025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .  
  
2. `#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [#Region yönergesi](../directives/region-directive.md)

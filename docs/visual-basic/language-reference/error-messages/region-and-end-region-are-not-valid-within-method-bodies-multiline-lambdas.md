---
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162290"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>BC32025: ' #Region ' ve ' #End Region ' deyimleri metot gövdeleri/çok satırlı Lambdalar içinde geçerli değildir

`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir. Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.

 **Hata kimliği:** BC32025

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .

2. `#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [#Region yönergesi](../directives/region-directive.md)

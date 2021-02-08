---
description: "Hakkında daha fazla bilgi edinin: BC32025: ' #Region ' ve ' #End Region ' deyimleri metot gövdeleri/çok satırlı Lambdalar içinde geçerli değildir"
title: "'#Region' ve '#End Region' deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 0746b9caf677699d6fbbf0c5a7063b1b33d86f3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792030"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>BC32025: ' #Region ' ve ' #End Region ' deyimleri metot gövdeleri/çok satırlı Lambdalar içinde geçerli değildir

`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir. Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.

 **Hata kimliği:** BC32025

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .

2. `#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [#Region yönergesi](../directives/region-directive.md)

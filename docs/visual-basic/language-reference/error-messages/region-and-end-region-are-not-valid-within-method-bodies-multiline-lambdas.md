---
title: "&#39; #Region &#39; ve &#39; #End Region &#39; deyimleri yöntem gövdeleri çok satırlı lambdalar içinde geçerli değildir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords: BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39; #Region &#39; ve &#39; #End Region &#39; deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir
`#Region` Bloğu bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir. Daraltılabilir bir bölgedeki bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.  
  
 **Hata Kimliği:** BC32025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Önceki yordam ile düzgün şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.  
  
2.  Emin `#Region` ve `#End Region` yönergeleri olan aynı kod bloğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)

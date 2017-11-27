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
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="2ef70-102">&#39; #Region &#39; ve &#39; #End Region &#39; deyimleri yöntem gövdeleri/çok satırlı lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="2ef70-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="2ef70-103">`#Region` Bloğu bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ef70-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="2ef70-104">Daraltılabilir bir bölgedeki bir veya daha fazla yordamlar içerebilir, ancak bunu başlayamaz veya bitemez bir yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="2ef70-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="2ef70-105">**Hata Kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="2ef70-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ef70-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2ef70-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2ef70-107">Önceki yordam ile düzgün şekilde sonlandırıldığından emin olun bir `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2ef70-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="2ef70-108">Emin `#Region` ve `#End Region` yönergeleri olan aynı kod bloğunda.</span><span class="sxs-lookup"><span data-stu-id="2ef70-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef70-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef70-109">See Also</span></span>  
 [<span data-ttu-id="2ef70-110">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="2ef70-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

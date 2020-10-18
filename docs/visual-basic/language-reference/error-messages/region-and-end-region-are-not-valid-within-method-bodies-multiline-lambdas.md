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
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="d081a-102">BC32025: ' #Region ' ve ' #End Region ' deyimleri metot gövdeleri/çok satırlı Lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="d081a-102">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="d081a-103">`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d081a-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="d081a-104">Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.</span><span class="sxs-lookup"><span data-stu-id="d081a-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="d081a-105">**Hata kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="d081a-105">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d081a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d081a-106">To correct this error</span></span>

1. <span data-ttu-id="d081a-107">Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="d081a-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="d081a-108">`#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d081a-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="d081a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d081a-109">See also</span></span>

- [<span data-ttu-id="d081a-110">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="d081a-110">#Region Directive</span></span>](../directives/region-directive.md)

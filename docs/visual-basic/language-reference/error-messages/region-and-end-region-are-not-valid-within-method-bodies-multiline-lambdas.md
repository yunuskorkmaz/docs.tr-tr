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
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="0e549-103">BC32025: ' #Region ' ve ' #End Region ' deyimleri metot gövdeleri/çok satırlı Lambdalar içinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="0e549-103">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="0e549-104">`#Region`Blok bir sınıf, modül veya ad alanı düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e549-104">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="0e549-105">Daraltılabilir bir bölge bir veya daha fazla yordam içerebilir, ancak bir yordamın içinde başlayamaz veya bitemez.</span><span class="sxs-lookup"><span data-stu-id="0e549-105">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="0e549-106">**Hata kimliği:** BC32025</span><span class="sxs-lookup"><span data-stu-id="0e549-106">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0e549-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0e549-107">To correct this error</span></span>

1. <span data-ttu-id="0e549-108">Önceki yordamın bir veya ifadesiyle doğru şekilde sonlandırıldığı emin `End Function` olun `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="0e549-108">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="0e549-109">`#Region`Ve `#End Region` yönergelerinin aynı kod bloğunda bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e549-109">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e549-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e549-110">See also</span></span>

- [<span data-ttu-id="0e549-111">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="0e549-111">#Region Directive</span></span>](../directives/region-directive.md)

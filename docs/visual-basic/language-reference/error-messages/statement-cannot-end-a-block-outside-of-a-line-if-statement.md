---
title: "Deyimi, bir çizgi &#39; dışında blok bitemez, varsa &#39; deyimi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="5f330-102">Deyimi, bir çizgi &#39; dışında blok bitemez, varsa &#39; deyimi</span><span class="sxs-lookup"><span data-stu-id="5f330-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="5f330-103">Tek satırlı `If` deyimi içeren birkaç deyimleri biri olan iki nokta işareti (:), ayrılmış bir `End` tek satırlı dışında bir denetim bloğu bildirimi `If`.</span><span class="sxs-lookup"><span data-stu-id="5f330-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="5f330-104">Tek satırlı `If` deyimleri kullanmayın `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5f330-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="5f330-105">**Hata Kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="5f330-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f330-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5f330-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5f330-107">Tek satırlı taşıma `If` deyimi içeren denetim bloğu dışında `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5f330-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f330-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f330-108">See Also</span></span>  
 [<span data-ttu-id="5f330-109">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="5f330-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

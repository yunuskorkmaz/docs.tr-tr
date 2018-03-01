---
title: "&#39; Modül &#39; deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="21cf2-102">&#39; Modül &#39; deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="21cf2-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="21cf2-103">`Module`deyimler, kaynak dosyanızın en üstte görünmelidir hemen sonra `Option` ve `Imports` deyimleri, genel öznitelikler ve ad alanı bildirimleri, ancak diğer tüm bildirimleri öncesinde.</span><span class="sxs-lookup"><span data-stu-id="21cf2-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="21cf2-104">**Hata Kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="21cf2-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21cf2-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="21cf2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="21cf2-106">Taşıma `Module` ad alanı bildirimini veya kaynak dosyanın en üstüne ifadesine.</span><span class="sxs-lookup"><span data-stu-id="21cf2-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cf2-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21cf2-107">See Also</span></span>  
 [<span data-ttu-id="21cf2-108">Module deyimi</span><span class="sxs-lookup"><span data-stu-id="21cf2-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

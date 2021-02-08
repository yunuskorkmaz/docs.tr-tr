---
description: "Hakkında daha fazla bilgi edinin: BC30481: ' class ' ifadesinin eşleşen bir ' End Class ile bitmesi gerekir"
title: "'Class' deyimi eşleşen bir 'End Class' ile bitmelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: b0d2d89e9e3549b24f9c923e271b15b3b02026b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796788"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="ff3a7-103">BC30481: ' class ' ifadesinin eşleşen bir ' End Class ' ile bitmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="ff3a7-103">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="ff3a7-104">`Class` bir bloğu başlatmak için kullanılır `Class` ; Bu nedenle, bloğu sonlandıran eşleşen bir deyimle birlikte yalnızca bloğun başlangıcında görünebilirler `End Class` .</span><span class="sxs-lookup"><span data-stu-id="ff3a7-104">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="ff3a7-105">Bir yedekli `Class` deyiminiz var veya kendi bloğundan sonlandırılamıyor `Class` `End Class` .</span><span class="sxs-lookup"><span data-stu-id="ff3a7-105">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="ff3a7-106">**Hata kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="ff3a7-106">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ff3a7-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ff3a7-107">To correct this error</span></span>

- <span data-ttu-id="ff3a7-108">Gereksiz deyimin yerini bulun ve kaldırın `Class` .</span><span class="sxs-lookup"><span data-stu-id="ff3a7-108">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="ff3a7-109">`Class`Bloğu eşleştirme ile sonuçlandırma `End Class` .</span><span class="sxs-lookup"><span data-stu-id="ff3a7-109">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff3a7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff3a7-110">See also</span></span>

- [<span data-ttu-id="ff3a7-111">End \<keyword> ekstresi</span><span class="sxs-lookup"><span data-stu-id="ff3a7-111">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="ff3a7-112">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ff3a7-112">Class Statement</span></span>](../statements/class-statement.md)

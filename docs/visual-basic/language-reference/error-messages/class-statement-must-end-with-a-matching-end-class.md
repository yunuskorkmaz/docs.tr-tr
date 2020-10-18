---
title: "'Class' deyimi eşleşen bir 'End Class' ile bitmelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163200"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="adc31-102">BC30481: ' class ' ifadesinin eşleşen bir ' End Class ' ile bitmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="adc31-102">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="adc31-103">`Class` bir bloğu başlatmak için kullanılır `Class` ; Bu nedenle, bloğu sonlandıran eşleşen bir deyimle birlikte yalnızca bloğun başlangıcında görünebilirler `End Class` .</span><span class="sxs-lookup"><span data-stu-id="adc31-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="adc31-104">Bir yedekli `Class` deyiminiz var veya kendi bloğundan sonlandırılamıyor `Class` `End Class` .</span><span class="sxs-lookup"><span data-stu-id="adc31-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="adc31-105">**Hata kimliği:** BC30481</span><span class="sxs-lookup"><span data-stu-id="adc31-105">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="adc31-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="adc31-106">To correct this error</span></span>

- <span data-ttu-id="adc31-107">Gereksiz deyimin yerini bulun ve kaldırın `Class` .</span><span class="sxs-lookup"><span data-stu-id="adc31-107">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="adc31-108">`Class`Bloğu eşleştirme ile sonuçlandırma `End Class` .</span><span class="sxs-lookup"><span data-stu-id="adc31-108">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="adc31-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adc31-109">See also</span></span>

- [<span data-ttu-id="adc31-110">End \<keyword> ekstresi</span><span class="sxs-lookup"><span data-stu-id="adc31-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="adc31-111">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="adc31-111">Class Statement</span></span>](../statements/class-statement.md)

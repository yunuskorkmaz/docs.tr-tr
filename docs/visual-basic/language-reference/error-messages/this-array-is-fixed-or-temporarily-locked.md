---
title: "Bu dizi sabit veya geçici olarak kilitli (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="fdba0-102">Bu dizi sabit veya geçici olarak kilitli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdba0-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="fdba0-103">Bu hata, aşağıdaki olası nedenleri vardır:</span><span class="sxs-lookup"><span data-stu-id="fdba0-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="fdba0-104">Kullanarak `ReDim` bir sabit boyutlu dizi öğelerinin sayısını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="fdba0-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="fdba0-105">İçinde bir öğe bağımsız değişken olarak bir yordama geçirildi bir modül düzeyi dinamik dizi redimensioning.</span><span class="sxs-lookup"><span data-stu-id="fdba0-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="fdba0-106">Bir öğenin aktarılırsa, dizi önlemek için kilitlenir yordamdaki başvuru parametre bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="fdba0-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="fdba0-107">Bir değer atamaya deneyen bir `Variant` içeren bir dizi değişken ancak `Variant` şu anda kilitli.</span><span class="sxs-lookup"><span data-stu-id="fdba0-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fdba0-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fdba0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="fdba0-109">Özgün dizi yerine ile bildirerek sabit dinamik olun `ReDim` (dizinin bir yordam içinde bildirilen varsa), ya da (array modülü düzeyinde bildirilirse. öğe sayısı belirtmeden bildirme</span><span class="sxs-lookup"><span data-stu-id="fdba0-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="fdba0-110">Sizin gerçekten modülündeki tüm yordamları içinde görünür olduğundan öğesi geçirmek gerekip gerekmeyeceğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fdba0-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="fdba0-111">Ne kilitleme belirlemek `Variant` ve çözüm.</span><span class="sxs-lookup"><span data-stu-id="fdba0-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdba0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdba0-112">See Also</span></span>  
 [<span data-ttu-id="fdba0-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="fdba0-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)

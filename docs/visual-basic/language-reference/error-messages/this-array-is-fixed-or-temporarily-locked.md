---
title: Bu dizi sabit veya geçici olarak kilitli (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f0b80e2be007ff44569365f37a2331f1ecd7a216
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839411"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="b235a-102">Bu dizi sabit veya geçici olarak kilitli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b235a-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="b235a-103">Bu hata, aşağıdaki olası nedenleri vardır:</span><span class="sxs-lookup"><span data-stu-id="b235a-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="b235a-104">Kullanarak `ReDim` sabit boyutlu dizi öğelerinin sayısını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b235a-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="b235a-105">İçinde bir öğe bağımsız değişken olarak bir yordamına geçirildi bir modül düzeyinde dinamik dizi redimensioning.</span><span class="sxs-lookup"><span data-stu-id="b235a-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="b235a-106">Bir öğe iletilmezse, dizi önlemek için kilitli yordamdaki başvuru parametresi bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="b235a-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="b235a-107">Bir değere atanmaya çalışılırken bir `Variant` içeren bir dizi değişkenini ancak `Variant` şu anda kilitli.</span><span class="sxs-lookup"><span data-stu-id="b235a-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b235a-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b235a-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="b235a-109">Özgün dizinin kendisiyle bildirerek sabit yerine dinamik hale getirmek `ReDim` (diziyi bir yordam içinde bildirilirse), ya da (diziyi Modül düzeyinde bildirilirse. öğe sayısını belirtmeden bildirme</span><span class="sxs-lookup"><span data-stu-id="b235a-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="b235a-110">Modüldeki tüm yordamları içinde görünür olduğundan, öğeyi geçirilecek ihtiyacınız olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b235a-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="b235a-111">Ne kilitleme belirlemek `Variant` ve çözüm.</span><span class="sxs-lookup"><span data-stu-id="b235a-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b235a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b235a-112">See also</span></span>

- [<span data-ttu-id="b235a-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="b235a-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)

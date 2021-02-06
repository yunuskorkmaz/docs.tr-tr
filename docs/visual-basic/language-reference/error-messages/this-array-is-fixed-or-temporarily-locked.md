---
description: 'Daha fazla bilgi edinin: Bu dizi sabit veya geçici olarak kilitli (Visual Basic)'
title: Bu dizi sabit veya geçici olarak kilitli
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 034bcc23055f7fb3f707e1105589a4526e6f9009
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641221"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="80171-103">Bu dizi sabit veya geçici olarak kilitli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80171-103">This array is fixed or temporarily locked (Visual Basic)</span></span>

<span data-ttu-id="80171-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="80171-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="80171-105">`ReDim`Sabit boyutlu bir dizinin öğelerinin sayısını değiştirmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="80171-105">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="80171-106">Bir öğe için bağımsız değişken olarak geçirilen bir modül düzeyinde dinamik dizi yeniden boyutlama.</span><span class="sxs-lookup"><span data-stu-id="80171-106">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="80171-107">Bir öğe geçirilirse, işlem içindeki başvuru parametresi için bellek ayırmayı engellemek üzere dizi kilitlenir.</span><span class="sxs-lookup"><span data-stu-id="80171-107">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="80171-108">Bir dizi içeren bir değişkene değer atamaya çalışılıyor `Variant` , ancak `Variant` Şu anda kilitli.</span><span class="sxs-lookup"><span data-stu-id="80171-108">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80171-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="80171-109">To correct this error</span></span>  
  
1. <span data-ttu-id="80171-110">Özgün diziyi, ile bildirerek sabit yerine dinamik yapın `ReDim` (dizi bir yordam içinde bildirilirse) veya öğe sayısını belirtmeden (dizi modül düzeyinde bildirilirse).</span><span class="sxs-lookup"><span data-stu-id="80171-110">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="80171-111">Modüldeki tüm yordamlarda görünür olduğundan, gerçekten öğeyi iletmeniz gerekip gerekmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="80171-111">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="80171-112">Neyi kilitleyeceğini `Variant` ve bu öğeyi nasıl yaptığını saptayın.</span><span class="sxs-lookup"><span data-stu-id="80171-112">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80171-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80171-113">See also</span></span>

- [<span data-ttu-id="80171-114">Diziler</span><span class="sxs-lookup"><span data-stu-id="80171-114">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)

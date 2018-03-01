---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="f1ebd-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1ebd-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="f1ebd-103">Dizi değişkenleri serbest bırakır ve bunların öğeler için kullanılan bellek ayırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ebd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1ebd-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="f1ebd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f1ebd-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="f1ebd-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-106">Required.</span></span> <span data-ttu-id="f1ebd-107">Dizi değişkenleri silinmesi listesi.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-107">List of array variables to be erased.</span></span> <span data-ttu-id="f1ebd-108">Birden çok değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1ebd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1ebd-109">Remarks</span></span>  
 <span data-ttu-id="f1ebd-110">`Erase` Deyimi yalnızca yordamı düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="f1ebd-111">Bu yordam içindeki ancak düzeyinde sınıfı veya modülü diziler serbest bırakabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="f1ebd-112">`Erase` Açıklamadır atama için eşdeğer `Nothing` her bir dizi değişken için.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ebd-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1ebd-113">Example</span></span>  
 <span data-ttu-id="f1ebd-114">Aşağıdaki örnek kullanır `Erase` dizilerinin temizlemek ve bunların belleği boşaltmak için deyimi (1000 ve 100 depolama öğeleri, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="f1ebd-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="f1ebd-115">`ReDim` Sonra deyim üç boyutlu diziye yeni bir dizi örnek atar.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f1ebd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ebd-116">See Also</span></span>  
 [<span data-ttu-id="f1ebd-117">Hiçbir şey</span><span class="sxs-lookup"><span data-stu-id="f1ebd-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="f1ebd-118">ReDim deyimi</span><span class="sxs-lookup"><span data-stu-id="f1ebd-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)

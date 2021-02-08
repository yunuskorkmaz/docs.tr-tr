---
description: ': Erase açıklaması hakkında daha fazla bilgi edinin (Visual Basic)'
title: Erase Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 295abec89f3d69f8f2641a5a3d574a2d10f98474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769162"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="9d762-103">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d762-103">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="9d762-104">Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d762-104">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d762-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d762-105">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="9d762-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9d762-106">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="9d762-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d762-107">Required.</span></span> <span data-ttu-id="9d762-108">Silinecek dizi değişkenlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="9d762-108">List of array variables to be erased.</span></span> <span data-ttu-id="9d762-109">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9d762-109">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d762-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d762-110">Remarks</span></span>  

 <span data-ttu-id="9d762-111">`Erase`Deyimde yalnızca yordam düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="9d762-111">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="9d762-112">Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.</span><span class="sxs-lookup"><span data-stu-id="9d762-112">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="9d762-113">`Erase`Deyimleri `Nothing` her dizi değişkenine atamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9d762-113">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d762-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d762-114">Example</span></span>  

 <span data-ttu-id="9d762-115">Aşağıdaki örnek, iki diziyi `Erase` temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d762-115">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="9d762-116">`ReDim`Daha sonra ifade, üç boyutlu diziye yeni bir dizi örneği atar.</span><span class="sxs-lookup"><span data-stu-id="9d762-116">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="9d762-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d762-117">See also</span></span>

- [<span data-ttu-id="9d762-118">Nothing</span><span class="sxs-lookup"><span data-stu-id="9d762-118">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="9d762-119">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d762-119">ReDim Statement</span></span>](redim-statement.md)

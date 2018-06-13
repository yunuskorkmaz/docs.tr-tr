---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601799"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="42af8-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42af8-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="42af8-103">Dizi değişkenleri serbest bırakır ve bunların öğeler için kullanılan bellek ayırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42af8-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42af8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42af8-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="42af8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="42af8-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="42af8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="42af8-106">Required.</span></span> <span data-ttu-id="42af8-107">Dizi değişkenleri silinmesi listesi.</span><span class="sxs-lookup"><span data-stu-id="42af8-107">List of array variables to be erased.</span></span> <span data-ttu-id="42af8-108">Birden çok değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="42af8-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42af8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42af8-109">Remarks</span></span>  
 <span data-ttu-id="42af8-110">`Erase` Deyimi yalnızca yordamı düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="42af8-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="42af8-111">Bu yordam içindeki ancak düzeyinde sınıfı veya modülü diziler serbest bırakabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="42af8-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="42af8-112">`Erase` Açıklamadır atama için eşdeğer `Nothing` her bir dizi değişken için.</span><span class="sxs-lookup"><span data-stu-id="42af8-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42af8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="42af8-113">Example</span></span>  
 <span data-ttu-id="42af8-114">Aşağıdaki örnek kullanır `Erase` dizilerinin temizlemek ve bunların belleği boşaltmak için deyimi (1000 ve 100 depolama öğeleri, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="42af8-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="42af8-115">`ReDim` Sonra deyim üç boyutlu diziye yeni bir dizi örnek atar.</span><span class="sxs-lookup"><span data-stu-id="42af8-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="42af8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42af8-116">See Also</span></span>  
 [<span data-ttu-id="42af8-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="42af8-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="42af8-118">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="42af8-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)

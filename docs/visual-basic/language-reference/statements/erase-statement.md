---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583396"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="bf5ff-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf5ff-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="bf5ff-103">Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf5ff-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="bf5ff-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bf5ff-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="bf5ff-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-106">Required.</span></span> <span data-ttu-id="bf5ff-107">Silinecek dizi değişkenlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-107">List of array variables to be erased.</span></span> <span data-ttu-id="bf5ff-108">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5ff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf5ff-109">Remarks</span></span>  
 <span data-ttu-id="bf5ff-110">@No__t_0 deyimleri yalnızca yordam düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="bf5ff-111">Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="bf5ff-112">@No__t_0 deyimin her dizi değişkenine `Nothing` atamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf5ff-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf5ff-113">Example</span></span>  
 <span data-ttu-id="bf5ff-114">Aşağıdaki örnek, iki diziyi temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için `Erase` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="bf5ff-115">@No__t_0 deyimleri, üç boyutlu diziye yeni bir dizi örneği atar.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="bf5ff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5ff-116">See also</span></span>

- [<span data-ttu-id="bf5ff-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="bf5ff-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="bf5ff-118">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf5ff-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)

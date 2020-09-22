---
title: Erase Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873283"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="d0b48-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0b48-102">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="d0b48-103">Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0b48-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0b48-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="d0b48-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0b48-105">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="d0b48-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0b48-106">Required.</span></span> <span data-ttu-id="d0b48-107">Silinecek dizi değişkenlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="d0b48-107">List of array variables to be erased.</span></span> <span data-ttu-id="d0b48-108">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="d0b48-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b48-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0b48-109">Remarks</span></span>  

 <span data-ttu-id="d0b48-110">`Erase`Deyimde yalnızca yordam düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="d0b48-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="d0b48-111">Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.</span><span class="sxs-lookup"><span data-stu-id="d0b48-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="d0b48-112">`Erase`Deyimleri `Nothing` her dizi değişkenine atamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d0b48-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b48-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0b48-113">Example</span></span>  

 <span data-ttu-id="d0b48-114">Aşağıdaki örnek, iki diziyi `Erase` temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0b48-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="d0b48-115">`ReDim`Daha sonra ifade, üç boyutlu diziye yeni bir dizi örneği atar.</span><span class="sxs-lookup"><span data-stu-id="d0b48-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b48-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b48-116">See also</span></span>

- [<span data-ttu-id="d0b48-117">Yapma</span><span class="sxs-lookup"><span data-stu-id="d0b48-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="d0b48-118">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d0b48-118">ReDim Statement</span></span>](redim-statement.md)

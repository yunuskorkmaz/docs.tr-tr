---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522446"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="e9ab0-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9ab0-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="e9ab0-103">Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan bellek ayırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ab0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9ab0-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="e9ab0-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e9ab0-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="e9ab0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-106">Required.</span></span> <span data-ttu-id="e9ab0-107">Silinecek şekilde dizi değişkenleri listesi.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-107">List of array variables to be erased.</span></span> <span data-ttu-id="e9ab0-108">Birden fazla değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9ab0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9ab0-109">Remarks</span></span>  
 <span data-ttu-id="e9ab0-110">`Erase` Deyimi yalnızca yordamı düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="e9ab0-111">Başka bir deyişle, bir yordam içinde ancak sınıf veya modül düzeyinde diziler serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="e9ab0-112">`Erase` Deyimi, atama için `Nothing` her dizi değişkeni için.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ab0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9ab0-113">Example</span></span>  
 <span data-ttu-id="e9ab0-114">Aşağıdaki örnekte `Erase` dizilerinin temizleyin ve kendi bellek boş deyim (1000 ve 100 depolama öğeleri sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="e9ab0-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="e9ab0-115">`ReDim` İfadesi üç boyutlu diziye yeni bir dizi örneği atar.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9ab0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-116">See also</span></span>
- [<span data-ttu-id="e9ab0-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="e9ab0-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="e9ab0-118">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="e9ab0-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)

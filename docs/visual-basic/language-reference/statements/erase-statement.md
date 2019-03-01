---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 5828e28b84ec62c7ed674757090806d73c61caea
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966742"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="3278a-102">Erase Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3278a-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="3278a-103">Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan bellek ayırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3278a-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3278a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3278a-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="3278a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3278a-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="3278a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3278a-106">Required.</span></span> <span data-ttu-id="3278a-107">Silinecek şekilde dizi değişkenleri listesi.</span><span class="sxs-lookup"><span data-stu-id="3278a-107">List of array variables to be erased.</span></span> <span data-ttu-id="3278a-108">Birden fazla değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3278a-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3278a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3278a-109">Remarks</span></span>  
 <span data-ttu-id="3278a-110">`Erase` Deyimi yalnızca yordamı düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="3278a-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="3278a-111">Başka bir deyişle, bir yordam içinde ancak sınıf veya modül düzeyinde diziler serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3278a-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="3278a-112">`Erase` Deyimi, atama için `Nothing` her dizi değişkeni için.</span><span class="sxs-lookup"><span data-stu-id="3278a-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3278a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3278a-113">Example</span></span>  
 <span data-ttu-id="3278a-114">Aşağıdaki örnekte `Erase` dizilerinin temizleyin ve kendi bellek boş deyim (1000 ve 100 depolama öğeleri sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="3278a-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="3278a-115">`ReDim` İfadesi üç boyutlu diziye yeni bir dizi örneği atar.</span><span class="sxs-lookup"><span data-stu-id="3278a-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="3278a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3278a-116">See also</span></span>
- [<span data-ttu-id="3278a-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="3278a-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="3278a-118">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="3278a-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)

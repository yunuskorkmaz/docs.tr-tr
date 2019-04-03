---
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815881"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="0f7a4-102">Tür '\<variablename >' döngü sınırları ve step değişkeni aynı türe genişletmek değil çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="0f7a4-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="0f7a4-103">Yazdığınız bir `For...Next` döngü içinde derleyici olamaz Infer döngü denetim değişkeni için bir veri türü aşağıdaki koşulların geçerli olması için:</span><span class="sxs-lookup"><span data-stu-id="0f7a4-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="0f7a4-104">Döngü denetim değişkeni veri türü ile belirtilmemiş bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="0f7a4-105">Döngü sınırları ve step değişkeni en az iki veri türü içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="0f7a4-106">Veri türleri arasında standart dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="0f7a4-107">Bu nedenle, derleyici bir döngü denetim değişkeni veri türü çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="0f7a4-108">Aşağıdaki örnekte, step değişkeni bir karakterse ve döngü sınırları hem tam sayılardır.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="0f7a4-109">Karakterler ve tam sayılar arasında standart dönüştürme olmadığından, bu hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="0f7a4-110">**Hata Kimliği:** BC30982</span><span class="sxs-lookup"><span data-stu-id="0f7a4-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f7a4-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0f7a4-111">To correct this error</span></span>  
  
-   <span data-ttu-id="0f7a4-112">Döngü sınırları ve step değişkeni gerektiğinde türlerini değiştirin, böylece en az bir tanesi, diğerleri için genişletmek bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="0f7a4-113">Önceki örnekte türünü değiştirme `stepVar` için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="0f7a4-114">—veya—</span><span class="sxs-lookup"><span data-stu-id="0f7a4-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="0f7a4-115">Döngü sınırları ve step değişkeni uygun türe dönüştürmek için açık dönüştürme işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="0f7a4-116">Önceki örnekte, geçerli `Val` işlevi `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f7a4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f7a4-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="0f7a4-118">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f7a4-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="0f7a4-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0f7a4-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="0f7a4-120">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="0f7a4-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="0f7a4-121">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f7a4-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="0f7a4-122">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0f7a4-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0f7a4-123">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="0f7a4-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

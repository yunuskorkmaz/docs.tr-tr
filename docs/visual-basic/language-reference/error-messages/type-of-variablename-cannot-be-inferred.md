---
title: "Tür &#39; &lt;variablename&gt;&#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="00b18-102">Tür &#39; &lt;variablename&gt;&#39; döngü sınırları ve adım değişken için aynı türde genişletmek değil çünkü çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="00b18-102">Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="00b18-103">Yazdığınız bir `For...Next` döngü içinde derleyici olamaz Infer for döngüsü denetim değişkeni için bir veri türü aşağıdaki koşulların geçerli olması için:</span><span class="sxs-lookup"><span data-stu-id="00b18-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="00b18-104">For döngüsü denetim değişkeni veri türü ile belirtilmemiş bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="00b18-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="00b18-105">Döngü sınırları ve adım değişkeni en az iki veri türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="00b18-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="00b18-106">Hiçbir standart dönüşümler veri türleri arasında mevcut.</span><span class="sxs-lookup"><span data-stu-id="00b18-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="00b18-107">Bu nedenle, derleyici bir döngünün denetim değişkeninin veri türü gösterilemiyor.</span><span class="sxs-lookup"><span data-stu-id="00b18-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="00b18-108">Aşağıdaki örnekte, adım değişken karakter ve döngü sınırları iki tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00b18-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="00b18-109">Karakterler ve tamsayılar arasında standart dönüştürme olduğundan, bu hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="00b18-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="00b18-110">**Hata Kimliği:** BC30982</span><span class="sxs-lookup"><span data-stu-id="00b18-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00b18-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="00b18-111">To correct this error</span></span>  
  
-   <span data-ttu-id="00b18-112">En az biri diğerleri genişletmek için bir tür şekilde türlerini döngü sınırları ve adım değişkeni gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="00b18-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="00b18-113">Önceki örnekte türünü değiştirme `stepVar` için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="00b18-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="00b18-114">—veya—</span><span class="sxs-lookup"><span data-stu-id="00b18-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="00b18-115">Açık dönüşüm işlevleri adım değişken ve döngü sınırlarını uygun türlerine dönüştürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="00b18-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="00b18-116">Önceki örnekte, geçerli `Val` için işlev `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="00b18-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="00b18-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00b18-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="00b18-118">İçin... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="00b18-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="00b18-119">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="00b18-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="00b18-120">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="00b18-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="00b18-121">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="00b18-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="00b18-122">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="00b18-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="00b18-123">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="00b18-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

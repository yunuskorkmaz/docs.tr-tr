---
title: Değişken &#39; &lt;variablename&gt; &#39; kapsayan bir blok içinde bir değişken gizliyor
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 23ec659535b71ee9af189f5c4fec0dec2bb1cd8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719436"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="51a59-102">Değişken &#39; &lt;variablename&gt; &#39; kapsayan bir blok içinde bir değişken gizliyor</span><span class="sxs-lookup"><span data-stu-id="51a59-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="51a59-103">İçine bir blokta bir değişkeni başka bir yerel değişken aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="51a59-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="51a59-104">**Hata Kimliği:** BC30616</span><span class="sxs-lookup"><span data-stu-id="51a59-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51a59-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="51a59-105">To correct this error</span></span>  
  
-   <span data-ttu-id="51a59-106">Böylece, aynı diğer herhangi bir yerel değişkenler değil kapalı bloktaki değişkeni yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="51a59-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="51a59-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="51a59-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="51a59-108">Bu hatanın yaygın bir nedeni kullanımıdır `Catch e As Exception` içinde bir olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="51a59-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="51a59-109">Bu durumda, ad `Catch` bloğu değişkeni `ex` yerine `e`.</span><span class="sxs-lookup"><span data-stu-id="51a59-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="51a59-110">Bu hatanın başka bir ortak kaynak içinde bildirilen yerel değişken erişme denemesi, bir `Try` ayrı bir engelleme `Catch` blok.</span><span class="sxs-lookup"><span data-stu-id="51a59-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="51a59-111">Bunu düzeltmek için değişken dışında bildirmek `Try...Catch...Finally` yapısı.</span><span class="sxs-lookup"><span data-stu-id="51a59-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a59-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51a59-112">See also</span></span>
- [<span data-ttu-id="51a59-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="51a59-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="51a59-114">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="51a59-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)

---
title: "Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39; Servis talebi &#39;seçin; deyimi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="7e331-102">Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39; Servis talebi &#39;seçin; deyimi</span><span class="sxs-lookup"><span data-stu-id="7e331-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="7e331-103">Test ifadesinde lambda ifadesi kullanamaz bir `Select Case` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7e331-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="7e331-104">Lambda ifadesi tanımları dönüş işlevler ve test ifadesi bir `Select Case` deyimi bir başlangıç veri türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e331-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="7e331-105">Aşağıdaki kod bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="7e331-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="7e331-106">**Hata Kimliği:** BC36635</span><span class="sxs-lookup"><span data-stu-id="7e331-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e331-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7e331-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7e331-108">Farklı bir koşullu yapım olup olmadığını belirlemek için kodunuzu inceleyin gibi bir `If...Then...Else` deyimi, sizin için çalışması.</span><span class="sxs-lookup"><span data-stu-id="7e331-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="7e331-109">Bir işlevi çağırmak aşağıdaki kodda gösterildiği gibi amaçladığınız:</span><span class="sxs-lookup"><span data-stu-id="7e331-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e331-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e331-110">See Also</span></span>  
 [<span data-ttu-id="7e331-111">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7e331-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="7e331-112">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="7e331-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="7e331-113">Seçin... Case deyimi</span><span class="sxs-lookup"><span data-stu-id="7e331-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)

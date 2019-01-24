---
title: Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700227"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="0f918-102">Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi</span><span class="sxs-lookup"><span data-stu-id="0f918-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="0f918-103">Bir lambda ifadesi içindeki test ifade kullanamazsınız bir `Select Case` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0f918-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="0f918-104">Lambda ifadesi tanımlarına dönüş işlevleri ve test ifadesi bir `Select Case` deyimi, bir başlangıç veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f918-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="0f918-105">Aşağıdaki kod bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="0f918-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="0f918-106">**Hata Kimliği:** BC36635</span><span class="sxs-lookup"><span data-stu-id="0f918-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f918-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0f918-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0f918-108">Belirleme farklı bir koşullu yapı, programınızın kodunu incelemek gibi bir `If...Then...Else` deyimi, sizin için çalışması.</span><span class="sxs-lookup"><span data-stu-id="0f918-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="0f918-109">Bir işlevi çağırmak aşağıdaki kodda gösterildiği gibi amaçladığınız:</span><span class="sxs-lookup"><span data-stu-id="0f918-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f918-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f918-110">See also</span></span>
- [<span data-ttu-id="0f918-111">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="0f918-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0f918-112">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f918-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="0f918-113">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f918-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)

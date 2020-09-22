---
title: Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 9f200ea44e7505c407c7df56e596435024394875
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873870"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="37372-102">Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="37372-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>

<span data-ttu-id="37372-103">Bir deyimde test ifadesi için lambda ifadesi kullanamazsınız `Select Case` .</span><span class="sxs-lookup"><span data-stu-id="37372-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="37372-104">Lambda ifade tanımları dönüş işlevleri ve bir deyimin test ifadesi bir `Select Case` Öğesel veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37372-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="37372-105">Aşağıdaki kod bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="37372-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="37372-106">**Hata kimliği:** BC36635</span><span class="sxs-lookup"><span data-stu-id="37372-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37372-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="37372-107">To correct this error</span></span>  
  
- <span data-ttu-id="37372-108">Bir bildirim gibi farklı bir koşullu oluşturma sizin için çalışıp çalışmadığını anlamak için kodunuzu inceleyin `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="37372-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
- <span data-ttu-id="37372-109">Aşağıdaki kodda gösterildiği gibi, işlevini çağırmanız istenebilir:</span><span class="sxs-lookup"><span data-stu-id="37372-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="37372-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37372-110">See also</span></span>

- [<span data-ttu-id="37372-111">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="37372-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="37372-112">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="37372-112">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="37372-113">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="37372-113">Select...Case Statement</span></span>](../statements/select-case-statement.md)

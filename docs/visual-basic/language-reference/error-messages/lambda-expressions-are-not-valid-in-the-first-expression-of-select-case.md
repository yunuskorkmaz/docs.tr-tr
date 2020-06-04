---
title: Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397369"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="f4cf3-102">Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="f4cf3-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="f4cf3-103">Bir deyimde test ifadesi için lambda ifadesi kullanamazsınız `Select Case` .</span><span class="sxs-lookup"><span data-stu-id="f4cf3-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="f4cf3-104">Lambda ifade tanımları dönüş işlevleri ve bir deyimin test ifadesi bir `Select Case` Öğesel veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4cf3-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="f4cf3-105">Aşağıdaki kod bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="f4cf3-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="f4cf3-106">**Hata kimliği:** BC36635</span><span class="sxs-lookup"><span data-stu-id="f4cf3-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4cf3-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f4cf3-107">To correct this error</span></span>  
  
- <span data-ttu-id="f4cf3-108">Bir bildirim gibi farklı bir koşullu oluşturma sizin için çalışıp çalışmadığını anlamak için kodunuzu inceleyin `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="f4cf3-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
- <span data-ttu-id="f4cf3-109">Aşağıdaki kodda gösterildiği gibi, işlevini çağırmanız istenebilir:</span><span class="sxs-lookup"><span data-stu-id="f4cf3-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4cf3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4cf3-110">See also</span></span>

- [<span data-ttu-id="f4cf3-111">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f4cf3-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="f4cf3-112">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4cf3-112">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="f4cf3-113">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4cf3-113">Select...Case Statement</span></span>](../statements/select-case-statement.md)

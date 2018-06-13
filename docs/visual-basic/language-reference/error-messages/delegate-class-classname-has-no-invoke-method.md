---
title: Temsilci sınıfı &#39; &lt;classname&gt; &#39; hiçbir Invoke yöntemi sahiptir, bu nedenle bu tür bir ifade bir yöntem çağrısı hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588836"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="28f00-102">Temsilci sınıfı &#39; &lt;classname&gt; &#39; hiçbir Invoke yöntemi sahiptir, bu nedenle bu tür bir ifade bir yöntem çağrısı hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="28f00-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="28f00-103">Çağrı `Invoke` bir temsilci başarısız oldu `Invoke` temsilci sınıf üzerinde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="28f00-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="28f00-104">**Hata Kimliği:** BC30220</span><span class="sxs-lookup"><span data-stu-id="28f00-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28f00-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="28f00-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="28f00-106">Temsilci sınıfının bir örneği ile oluşturulan olun bir `Dim` deyimi ve bir yordam temsilci örneğine atanan `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="28f00-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="28f00-107">Temsilci sınıfı uygulayan kodu bulun ve bunu uygulayan emin olun `Invoke` yordamı.</span><span class="sxs-lookup"><span data-stu-id="28f00-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f00-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28f00-108">See Also</span></span>  
 [<span data-ttu-id="28f00-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="28f00-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="28f00-110">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="28f00-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="28f00-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="28f00-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="28f00-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="28f00-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

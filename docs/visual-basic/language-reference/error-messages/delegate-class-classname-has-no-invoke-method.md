---
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 8339d038f845b8568f31f3068a98ccccf580aeae
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286656"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="afafd-102">Temsilci sınıfında\<SınıfAdı >' Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz sahip</span><span class="sxs-lookup"><span data-stu-id="afafd-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="afafd-103">Bir çağrı `Invoke` bir temsilci olduğundan başarısız oldu `Invoke` temsilci sınıfı üzerinde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="afafd-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="afafd-104">**Hata Kimliği:** BC30220</span><span class="sxs-lookup"><span data-stu-id="afafd-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="afafd-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="afafd-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="afafd-106">Temsilci sınıfının örneği ile oluşturulduğundan emin olun. bir `Dim` ifadesi ve bir yordam temsilci örneği ile atanan `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="afafd-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="afafd-107">Temsilci sınıfı uygulayan kod bulun ve bunu uygulayan emin `Invoke` yordamı.</span><span class="sxs-lookup"><span data-stu-id="afafd-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afafd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afafd-108">See also</span></span>
- [<span data-ttu-id="afafd-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="afafd-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="afafd-110">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="afafd-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="afafd-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="afafd-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="afafd-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="afafd-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

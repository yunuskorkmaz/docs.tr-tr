---
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321308"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="6e090-102">Temsilci sınıfında\<SınıfAdı >' Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz sahip</span><span class="sxs-lookup"><span data-stu-id="6e090-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="6e090-103">Bir çağrı `Invoke` bir temsilci olduğundan başarısız oldu `Invoke` temsilci sınıfı üzerinde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6e090-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="6e090-104">**Hata Kimliği:** BC30220</span><span class="sxs-lookup"><span data-stu-id="6e090-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e090-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6e090-105">To correct this error</span></span>  
  
1. <span data-ttu-id="6e090-106">Temsilci sınıfının örneği ile oluşturulduğundan emin olun. bir `Dim` ifadesi ve bir yordam temsilci örneği ile atanan `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="6e090-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="6e090-107">Temsilci sınıfı uygulayan kod bulun ve bunu uygulayan emin `Invoke` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6e090-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e090-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e090-108">See also</span></span>

- [<span data-ttu-id="6e090-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6e090-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="6e090-110">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e090-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="6e090-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="6e090-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="6e090-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e090-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

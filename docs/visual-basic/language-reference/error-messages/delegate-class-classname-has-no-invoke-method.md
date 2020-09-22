---
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: e6ad06262806088347c94b3040b743618a3b3695
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874497"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="6f9da-102">'\<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="6f9da-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="6f9da-103">Temsilci `Invoke` sınıfında uygulanmadığı için bir temsilci aracılığıyla yapılan çağrı başarısız oldu `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="6f9da-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="6f9da-104">**Hata kimliği:** BC30220</span><span class="sxs-lookup"><span data-stu-id="6f9da-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f9da-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6f9da-105">To correct this error</span></span>  
  
1. <span data-ttu-id="6f9da-106">Temsilci sınıfının bir örneğinin bir `Dim` ifadesiyle oluşturulduğundan ve bu işleç ile temsilci örneğine bir yordamın atandığından emin olun `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="6f9da-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="6f9da-107">Temsilci sınıfını uygulayan kodu bulun ve yordamı gerçekleştirdiğinden emin olun `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="6f9da-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9da-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f9da-108">See also</span></span>

- [<span data-ttu-id="6f9da-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6f9da-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="6f9da-110">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f9da-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="6f9da-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="6f9da-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="6f9da-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f9da-112">Dim Statement</span></span>](../statements/dim-statement.md)

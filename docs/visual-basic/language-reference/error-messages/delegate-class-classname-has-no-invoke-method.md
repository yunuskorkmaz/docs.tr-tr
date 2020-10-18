---
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162797"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="8b01d-102">BC30220: ' ' temsilci sınıfında \<classname> Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="8b01d-102">BC30220: Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="8b01d-103">Temsilci `Invoke` sınıfında uygulanmadığı için bir temsilci aracılığıyla yapılan çağrı başarısız oldu `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="8b01d-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>

 <span data-ttu-id="8b01d-104">**Hata kimliği:** BC30220</span><span class="sxs-lookup"><span data-stu-id="8b01d-104">**Error ID:** BC30220</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8b01d-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8b01d-105">To correct this error</span></span>

1. <span data-ttu-id="8b01d-106">Temsilci sınıfının bir örneğinin bir `Dim` ifadesiyle oluşturulduğundan ve bu işleç ile temsilci örneğine bir yordamın atandığından emin olun `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="8b01d-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>

2. <span data-ttu-id="8b01d-107">Temsilci sınıfını uygulayan kodu bulun ve yordamı gerçekleştirdiğinden emin olun `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="8b01d-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b01d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b01d-108">See also</span></span>

- [<span data-ttu-id="8b01d-109">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="8b01d-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="8b01d-110">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="8b01d-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="8b01d-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="8b01d-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="8b01d-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8b01d-112">Dim Statement</span></span>](../statements/dim-statement.md)

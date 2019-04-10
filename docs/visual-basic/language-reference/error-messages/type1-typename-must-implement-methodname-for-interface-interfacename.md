---
title: <type1>'<typename>'uygulamalıdır'<methodname>'interfaceiçin'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304915"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="7c904-102">\<type1 >'\<typename >' uygulamalıdır '\<yöntemAdı >' arabirimi için '\<InterfaceName >'</span><span class="sxs-lookup"><span data-stu-id="7c904-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="7c904-103">Bir sınıf veya yapı bir arabirim uygulamak talep ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="7c904-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="7c904-104">Her arabirimin üyesi uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c904-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="7c904-105">**Hata Kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="7c904-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c904-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7c904-106">To correct this error</span></span>  
  
1. <span data-ttu-id="7c904-107">Bir yordam aynı adı ve imzası arabirim içinde tanımlanmış olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="7c904-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="7c904-108">Eklediğinizden emin olun en az `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7c904-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="7c904-109">Ekleme bir `Implements` sonuna yan tümcesi `Function` veya `Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7c904-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="7c904-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7c904-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7c904-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c904-111">See also</span></span>

- [<span data-ttu-id="7c904-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="7c904-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="7c904-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="7c904-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

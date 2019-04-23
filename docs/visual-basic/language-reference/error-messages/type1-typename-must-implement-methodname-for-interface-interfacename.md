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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304915"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="28ed1-102">\<type1 >'\<typename >' uygulamalıdır '\<yöntemAdı >' arabirimi için '\<InterfaceName >'</span><span class="sxs-lookup"><span data-stu-id="28ed1-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="28ed1-103">Bir sınıf veya yapı bir arabirim uygulamak talep ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="28ed1-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="28ed1-104">Her arabirimin üyesi uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28ed1-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="28ed1-105">**Hata Kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="28ed1-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28ed1-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="28ed1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="28ed1-107">Bir yordam aynı adı ve imzası arabirim içinde tanımlanmış olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="28ed1-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="28ed1-108">Eklediğinizden emin olun en az `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="28ed1-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="28ed1-109">Ekleme bir `Implements` sonuna yan tümcesi `Function` veya `Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="28ed1-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="28ed1-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="28ed1-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28ed1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28ed1-111">See also</span></span>

- [<span data-ttu-id="28ed1-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="28ed1-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="28ed1-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="28ed1-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

---
title: <type1>'<typename>'uygulamalıdır'<methodname>'interfaceiçin'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: b8bcb16798284a09608ba6942226ef07c6859d4f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824211"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="a75be-102">\<type1 >'\<typename >' uygulamalıdır '\<yöntemAdı >' arabirimi için '\<InterfaceName >'</span><span class="sxs-lookup"><span data-stu-id="a75be-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="a75be-103">Bir sınıf veya yapı bir arabirim uygulamak talep ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="a75be-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="a75be-104">Her arabirimin üyesi uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a75be-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="a75be-105">**Hata Kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="a75be-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a75be-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a75be-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a75be-107">Bir yordam aynı adı ve imzası arabirim içinde tanımlanmış olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="a75be-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="a75be-108">Eklediğinizden emin olun en az `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a75be-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="a75be-109">Ekleme bir `Implements` sonuna yan tümcesi `Function` veya `Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a75be-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="a75be-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a75be-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a75be-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a75be-111">See also</span></span>

- [<span data-ttu-id="a75be-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="a75be-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="a75be-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a75be-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591594"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="98c82-102">\<type1 > ' \<typename > ', ' \<arabirimadı > ' arabirimi için ' \<methodname > ' uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="98c82-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="98c82-103">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="98c82-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="98c82-104">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98c82-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="98c82-105">**Hata KIMLIĞI:** BC30149</span><span class="sxs-lookup"><span data-stu-id="98c82-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98c82-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="98c82-106">To correct this error</span></span>  
  
1. <span data-ttu-id="98c82-107">Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin.</span><span class="sxs-lookup"><span data-stu-id="98c82-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="98c82-108">En azından `End Function` veya `End Sub` ifadesini eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="98c82-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="98c82-109">@No__t-1 veya `Sub` ifadesinin sonuna `Implements` yan tümcesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98c82-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="98c82-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="98c82-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="98c82-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98c82-111">See also</span></span>

- [<span data-ttu-id="98c82-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="98c82-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="98c82-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="98c82-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

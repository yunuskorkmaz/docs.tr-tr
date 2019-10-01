---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<membername>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696892"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="512f1-102">\<type1 > ' \<typename > ', ' \<ınterfacename > ' arabirimi için ' \<membername > ' uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="512f1-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="512f1-103">' \<typename > ', ' \<ınterfacename > ' arabirimi için ' \<membername > ' uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="512f1-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="512f1-104">Uygulama özelliğinin eşleşen ' ReadOnly '/' WriteOnly ' belirticileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="512f1-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="512f1-105">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam, özellik veya olay uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="512f1-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="512f1-106">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="512f1-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="512f1-107">**Hata kimliği:** BC30154</span><span class="sxs-lookup"><span data-stu-id="512f1-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="512f1-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="512f1-108">To correct this error</span></span>  
  
1. <span data-ttu-id="512f1-109">Arabirimde tanımlanan aynı ada ve imzaya sahip bir üye bildirin.</span><span class="sxs-lookup"><span data-stu-id="512f1-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="512f1-110">En az `End Function`, `End Sub` veya `End Property` ifadesini eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="512f1-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="512f1-111">@No__t-1, `Sub`, `Property` veya `Event` deyimlerinin sonuna bir `Implements` yan tümcesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="512f1-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="512f1-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="512f1-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="512f1-113">Bir özellik uygularken, `ReadOnly` veya `WriteOnly` ' in arabirim tanımındaki ile aynı şekilde kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="512f1-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="512f1-114">Bir özellik uygularken, uygun şekilde `Get` ve `Set` yordamları bildirin.</span><span class="sxs-lookup"><span data-stu-id="512f1-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512f1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="512f1-115">See also</span></span>

- [<span data-ttu-id="512f1-116">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="512f1-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="512f1-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="512f1-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

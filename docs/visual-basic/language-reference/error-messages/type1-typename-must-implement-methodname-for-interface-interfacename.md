---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 8bf8872277ec901e066a8b950aaf3e61babfcc48
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872101"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="6413d-102">\<type1>'\<typename>', '\<interfacename>' arabirimi için '\<methodname>' uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="6413d-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="6413d-103">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="6413d-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="6413d-104">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6413d-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="6413d-105">**Hata kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="6413d-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6413d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6413d-106">To correct this error</span></span>  
  
1. <span data-ttu-id="6413d-107">Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin.</span><span class="sxs-lookup"><span data-stu-id="6413d-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="6413d-108">En azından veya ifadesini eklediğinizden emin olun `End Function` `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="6413d-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="6413d-109">`Implements`Or ifadesinin sonuna bir yan tümce ekleyin `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="6413d-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="6413d-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6413d-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6413d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6413d-111">See also</span></span>

- [<span data-ttu-id="6413d-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="6413d-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="6413d-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6413d-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

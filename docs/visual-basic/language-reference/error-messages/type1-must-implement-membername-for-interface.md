---
title: <type1>'<typename>', '<interfacename>' arabirimi için '<membername>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 7b74ee3a05000f5d6cd94176b48dea116b647a2a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872167"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="74343-102">\<type1>'\<typename>', '\<interfacename>' arabirimi için '\<membername>' uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="74343-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="74343-103">' ', ' ' \<typename> \<membername> arabirimi için ' ' uygulamalıdır \<interfacename> .</span><span class="sxs-lookup"><span data-stu-id="74343-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="74343-104">Uygulama özelliğinin eşleşen ' ReadOnly '/' WriteOnly ' belirticileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74343-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="74343-105">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam, özellik veya olay uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="74343-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="74343-106">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="74343-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="74343-107">**Hata kimliği:** BC30154</span><span class="sxs-lookup"><span data-stu-id="74343-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74343-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="74343-108">To correct this error</span></span>  
  
1. <span data-ttu-id="74343-109">Arabirimde tanımlanan aynı ada ve imzaya sahip bir üye bildirin.</span><span class="sxs-lookup"><span data-stu-id="74343-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="74343-110">En azından `End Function` , `End Sub` , veya ifadesini eklediğinizden emin olun `End Property` .</span><span class="sxs-lookup"><span data-stu-id="74343-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="74343-111">,, `Implements` `Function` `Sub` `Property` Veya ifadesinin sonuna bir yan tümce ekleyin `Event` .</span><span class="sxs-lookup"><span data-stu-id="74343-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="74343-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="74343-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="74343-113">Bir özellik uygularken, ya da ' `ReadOnly` `WriteOnly` nin arabirim tanımındaki ile aynı şekilde kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="74343-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="74343-114">Bir özellik uygularken, `Get` ve `Set` yordamları uygun şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="74343-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74343-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74343-115">See also</span></span>

- [<span data-ttu-id="74343-116">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="74343-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="74343-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="74343-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

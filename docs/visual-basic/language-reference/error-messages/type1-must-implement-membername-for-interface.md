---
description: "Hakkında daha fazla bilgi edinin: BC30154: ' ', ' ' <type1> <typename> <membername> arabirimi için ' ' uygulamalıdır <interfacename>"
title: <type1>'<typename>', '<interfacename>' arabirimi için '<membername>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: fc0cf8544984ddf41f1f91cb0bca90b630d9614d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473569"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="d5cd5-103">BC30154: ' ', ' ' \<type1> \<typename> \<membername> arabirimi için ' ' \<interfacename> uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="d5cd5-103">BC30154: \<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="d5cd5-104">' ', ' ' \<typename> \<membername> arabirimi için ' ' uygulamalıdır \<interfacename> .</span><span class="sxs-lookup"><span data-stu-id="d5cd5-104">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="d5cd5-105">Uygulama özelliğinin eşleşen ' ReadOnly '/' WriteOnly ' belirticileri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-105">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>

 <span data-ttu-id="d5cd5-106">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam, özellik veya olay uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-106">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="d5cd5-107">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-107">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="d5cd5-108">**Hata kimliği:** BC30154</span><span class="sxs-lookup"><span data-stu-id="d5cd5-108">**Error ID:** BC30154</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d5cd5-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d5cd5-109">To correct this error</span></span>

1. <span data-ttu-id="d5cd5-110">Arabirimde tanımlanan aynı ada ve imzaya sahip bir üye bildirin.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-110">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="d5cd5-111">En azından `End Function` , `End Sub` , veya ifadesini eklediğinizden emin olun `End Property` .</span><span class="sxs-lookup"><span data-stu-id="d5cd5-111">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>

2. <span data-ttu-id="d5cd5-112">,, `Implements` `Function` `Sub` `Property` Veya ifadesinin sonuna bir yan tümce ekleyin `Event` .</span><span class="sxs-lookup"><span data-stu-id="d5cd5-112">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="d5cd5-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d5cd5-113">For example:</span></span>

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. <span data-ttu-id="d5cd5-114">Bir özellik uygularken, ya da ' `ReadOnly` `WriteOnly` nin arabirim tanımındaki ile aynı şekilde kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-114">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>

4. <span data-ttu-id="d5cd5-115">Bir özellik uygularken, `Get` ve `Set` yordamları uygun şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-115">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5cd5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5cd5-116">See also</span></span>

- [<span data-ttu-id="d5cd5-117">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="d5cd5-117">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="d5cd5-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d5cd5-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

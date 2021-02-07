---
description: "Hakkında daha fazla bilgi edinin: BC30149: <type1> ' <typename> ' <methodname> arabirim için ' ' uygulamalıdır<interfacename>"
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 34635cbe5b8736d273d5972a1bb83aa3d975490b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675019"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="2d8d4-103">BC30149: ' ', ' ' \<type1> \<typename> \<methodname> arabirimi için ' ' \<interfacename> uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="2d8d4-103">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="2d8d4-104">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="2d8d4-104">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="2d8d4-105">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d8d4-105">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="2d8d4-106">**Hata kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="2d8d4-106">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2d8d4-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2d8d4-107">To correct this error</span></span>

1. <span data-ttu-id="2d8d4-108">Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin.</span><span class="sxs-lookup"><span data-stu-id="2d8d4-108">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="2d8d4-109">En azından veya ifadesini eklediğinizden emin olun `End Function` `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="2d8d4-109">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="2d8d4-110">`Implements`Or ifadesinin sonuna bir yan tümce ekleyin `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="2d8d4-110">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="2d8d4-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2d8d4-111">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="2d8d4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d8d4-112">See also</span></span>

- [<span data-ttu-id="2d8d4-113">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d8d4-113">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="2d8d4-114">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="2d8d4-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

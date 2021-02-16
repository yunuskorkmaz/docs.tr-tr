---
description: "Hakkında daha fazla bilgi edinin: BC30149: ' ', ' ' <type1> <typename> <methodname> arabirimi için ' ' uygulamalıdır <interfacename>"
title: <type1>'<typename>', '<interfacename>' arabirimi için '<methodname>' uygulamalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: b2fb7f5ea019a86b18ea89456e353778e5246d2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473443"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="9eccd-103">BC30149: ' ', ' ' \<type1> \<typename> \<methodname> arabirimi için ' ' \<interfacename> uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="9eccd-103">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="9eccd-104">Bir sınıf veya yapı, arabirim uygulamak için talepler, ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="9eccd-104">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="9eccd-105">Arabirimin her üyesinin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eccd-105">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="9eccd-106">**Hata kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="9eccd-106">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9eccd-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9eccd-107">To correct this error</span></span>

1. <span data-ttu-id="9eccd-108">Arabirimde tanımlanan aynı ada ve imzaya sahip bir yordam bildirin.</span><span class="sxs-lookup"><span data-stu-id="9eccd-108">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="9eccd-109">En azından veya ifadesini eklediğinizden emin olun `End Function` `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="9eccd-109">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="9eccd-110">`Implements`Or ifadesinin sonuna bir yan tümce ekleyin `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9eccd-110">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="9eccd-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9eccd-111">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="9eccd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eccd-112">See also</span></span>

- [<span data-ttu-id="9eccd-113">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="9eccd-113">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="9eccd-114">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9eccd-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

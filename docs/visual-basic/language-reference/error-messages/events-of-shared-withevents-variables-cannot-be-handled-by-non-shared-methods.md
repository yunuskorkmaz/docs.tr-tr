---
description: 'Hakkında daha fazla bilgi edinin: BC30594: paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez'
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f9e8bf6e0d365c4ee747deb6be0e809904d87117
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796424"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="8c0ce-103">BC30594: paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez</span><span class="sxs-lookup"><span data-stu-id="8c0ce-103">BC30594: Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>

<span data-ttu-id="8c0ce-104">Değiştiriciyle belirtilen bir değişken `Shared` paylaşılan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="8c0ce-104">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="8c0ce-105">Paylaşılan değişken tam olarak bir depolama konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8c0ce-105">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="8c0ce-106">Değiştirici ile belirtilen bir değişken, `WithEvents` değişkenin ait olduğu türün, değişkenin oluşturulduğu olay kümesini işlediğini onaylar.</span><span class="sxs-lookup"><span data-stu-id="8c0ce-106">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="8c0ce-107">Değişkene bir değer atandığında, bildirim tarafından oluşturulan özellik `WithEvents` mevcut olay işleyicisinin kancalarını kaldırır ve yöntemi aracılığıyla yeni olay işleyicisini takar `Add` .</span><span class="sxs-lookup"><span data-stu-id="8c0ce-107">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>

 <span data-ttu-id="8c0ce-108">**Hata kimliği:** BC30594</span><span class="sxs-lookup"><span data-stu-id="8c0ce-108">**Error ID:** BC30594</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8c0ce-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8c0ce-109">To correct this error</span></span>

- <span data-ttu-id="8c0ce-110">Olay işleyicinizi bildirin `Shared` .</span><span class="sxs-lookup"><span data-stu-id="8c0ce-110">Declare your event handler `Shared`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c0ce-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c0ce-111">See also</span></span>

- [<span data-ttu-id="8c0ce-112">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="8c0ce-112">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="8c0ce-113">WithEvents</span><span class="sxs-lookup"><span data-stu-id="8c0ce-113">WithEvents</span></span>](../modifiers/withevents.md)

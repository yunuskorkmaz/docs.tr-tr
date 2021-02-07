---
description: "Hakkında daha fazla bilgi edinin: BC32005: deyimin bir satır ' If ' ifadesinin dışında bir blok sonlandırılamıyor"
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: afe856b2c2ea3fa1db029d35c5b876f5d67da411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731166"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="71fea-103">BC32005: deyimin bir satır ' If ' ifadesinin dışında bir blok sonlandırılamıyor</span><span class="sxs-lookup"><span data-stu-id="71fea-103">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="71fea-104">Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` .</span><span class="sxs-lookup"><span data-stu-id="71fea-104">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="71fea-105">Tek satırlı `If` deyimler `End If` deyimini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="71fea-105">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="71fea-106">**Hata kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="71fea-106">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="71fea-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="71fea-107">To correct this error</span></span>

- <span data-ttu-id="71fea-108">Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .</span><span class="sxs-lookup"><span data-stu-id="71fea-108">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="71fea-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71fea-109">See also</span></span>

- [<span data-ttu-id="71fea-110">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="71fea-110">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)

---
description: 'Şu konuda daha fazla bilgi edinin: BC30439: sabit ifade tür içinde gösterilemeyen tablo değil<typename>'
title: Sabit ifade '<typename>' türünde gösterilemez
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: 763ed8a414d8dda3e950ae85a4b1152a459518a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796749"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="279a0-103">BC30439: sabit ifade ' ' türünde gösterilemez \<typename></span><span class="sxs-lookup"><span data-stu-id="279a0-103">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="279a0-104">Genellikle aralığı taşdığı için hedef türüne sığmayan bir sabiti değerlendirmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="279a0-104">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="279a0-105">**Hata kimliği:** BC30439</span><span class="sxs-lookup"><span data-stu-id="279a0-105">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="279a0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="279a0-106">To correct this error</span></span>

1. <span data-ttu-id="279a0-107">Hedef türünü, sabiti işleyebilen bir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="279a0-107">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="279a0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="279a0-108">See also</span></span>

- [<span data-ttu-id="279a0-109">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="279a0-109">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="279a0-110">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="279a0-110">Constants and Enumerations</span></span>](../constants-and-enumerations.md)

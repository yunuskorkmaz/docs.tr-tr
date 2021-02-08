---
description: "Hakkında daha fazla bilgi edinin: BC30269: ' <methodname> ', aynı imzalara sahip birden fazla tanım içeriyor"
title: "'<methodname>' içinde aynı imzaya sahip birden fazla tanım var"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 7364ee7a308fab96afce268ff0c92cd45717f1bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795813"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="049d8-103">BC30269: ' \<methodname> ', aynı imzalara sahip birden fazla tanıma sahip</span><span class="sxs-lookup"><span data-stu-id="049d8-103">BC30269: '\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="049d8-104">Bir `Function` veya `Sub` yordam bildirimi, önceki bir bildirim olarak aynı yordam adı ve bağımsız değişken listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="049d8-104">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="049d8-105">Olası bir neden, özgün yordamı aşırı yükleme girişimdir.</span><span class="sxs-lookup"><span data-stu-id="049d8-105">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="049d8-106">Aşırı yüklenmiş yordamların farklı bağımsız değişken listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="049d8-106">Overloaded procedures must have different argument lists.</span></span>

 <span data-ttu-id="049d8-107">**Hata kimliği:** BC30269</span><span class="sxs-lookup"><span data-stu-id="049d8-107">**Error ID:** BC30269</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="049d8-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="049d8-108">To correct this error</span></span>

- <span data-ttu-id="049d8-109">Yordam adını veya bağımsız değişken listesini değiştirin veya yinelenen bildirimi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="049d8-109">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="049d8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="049d8-110">See also</span></span>

- [<span data-ttu-id="049d8-111">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="049d8-111">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="049d8-112">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="049d8-112">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

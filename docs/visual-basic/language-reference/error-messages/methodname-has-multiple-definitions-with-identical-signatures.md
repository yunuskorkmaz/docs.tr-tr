---
title: "'<methodname>' içinde aynı imzaya sahip birden fazla tanım var"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 663b22421d1a0e401cfb3c135c99bd097163a78b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160372"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="867a1-102">BC30269: ' \<methodname> ', aynı imzalara sahip birden fazla tanıma sahip</span><span class="sxs-lookup"><span data-stu-id="867a1-102">BC30269: '\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="867a1-103">Bir `Function` veya `Sub` yordam bildirimi, önceki bir bildirim olarak aynı yordam adı ve bağımsız değişken listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="867a1-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="867a1-104">Olası bir neden, özgün yordamı aşırı yükleme girişimdir.</span><span class="sxs-lookup"><span data-stu-id="867a1-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="867a1-105">Aşırı yüklenmiş yordamların farklı bağımsız değişken listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="867a1-105">Overloaded procedures must have different argument lists.</span></span>

 <span data-ttu-id="867a1-106">**Hata kimliği:** BC30269</span><span class="sxs-lookup"><span data-stu-id="867a1-106">**Error ID:** BC30269</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="867a1-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="867a1-107">To correct this error</span></span>

- <span data-ttu-id="867a1-108">Yordam adını veya bağımsız değişken listesini değiştirin veya yinelenen bildirimi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="867a1-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="867a1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="867a1-109">See also</span></span>

- [<span data-ttu-id="867a1-110">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="867a1-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="867a1-111">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="867a1-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

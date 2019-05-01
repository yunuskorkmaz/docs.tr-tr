---
title: "'<methodname>' içinde aynı imzaya sahip birden fazla tanım var"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: fe8d1d8e11e25bcd79894ed82a57dd06748c3d68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920906"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="bec85-102">'\<yöntemAdı >' aynı imzaya sahip birden fazla tanım var</span><span class="sxs-lookup"><span data-stu-id="bec85-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="bec85-103">A `Function` veya `Sub` yordam bildirimi, bir önceki bildirimi olarak aynı yordamı adı ve bağımsız değişken listesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="bec85-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="bec85-104">Olası nedenlerinden biri, özgün bir yordamı aşırı yükleme girişiminde olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bec85-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="bec85-105">Aşırı yüklenmiş yordamları farklı bağımsız değişken listeleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bec85-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="bec85-106">**Hata Kimliği:** BC30269</span><span class="sxs-lookup"><span data-stu-id="bec85-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bec85-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bec85-107">To correct this error</span></span>  
  
- <span data-ttu-id="bec85-108">Yordam adı veya bağımsız değişken listesiyle değiştirin veya yinelenen bildirimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bec85-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec85-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec85-109">See also</span></span>

- [<span data-ttu-id="bec85-110">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="bec85-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="bec85-111">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="bec85-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

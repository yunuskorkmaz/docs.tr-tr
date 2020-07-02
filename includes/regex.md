---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802863"
---

> [!WARNING]
> <span data-ttu-id="d369d-101"><xref:System.Text.RegularExpressions>Güvenilmeyen girişi işlemek için kullanırken bir zaman aşımı geçirin.</span><span class="sxs-lookup"><span data-stu-id="d369d-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="d369d-102">Kötü niyetli bir Kullanıcı, `RegularExpressions` [hizmet reddi saldırısına](https://www.us-cert.gov/ncas/tips/ST04-015)neden olacak giriş sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d369d-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="d369d-103">Zaman aşımını geçen ASP.NET Core Framework API 'Leri `RegularExpressions` .</span><span class="sxs-lookup"><span data-stu-id="d369d-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>

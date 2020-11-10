---
title: 'NETSDK1079: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. All paketi desteklenmez.'
description: Microsoft. AspNetCore. app 'ten geçişi çözme
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445803"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a><span data-ttu-id="d1c38-103">NETSDK1079: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. All paketi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d1c38-103">NETSDK1079: The Microsoft.AspNetCore.All package is not supported when targeting .NET Core 3.0 or higher.</span></span>

<span data-ttu-id="d1c38-104">**Bu makale için geçerlidir:** ✔️ .NET Core SDK 3.1.100 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="d1c38-104">**This article applies to:** ✔️ .NET Core SDK 3.1.100 and later versions</span></span>

<span data-ttu-id="d1c38-105">Şu durumlarda şu hata iletisini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d1c38-105">You may receive this error message when:</span></span>

- <span data-ttu-id="d1c38-106">ASP.NET Core bir projeyi .NET Core 2,2 veya daha önceki bir sürümden .NET Core 3,0 veya sonraki bir sürümüne yeniden hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1c38-106">You retarget an ASP.NET Core project from .NET Core 2.2 or earlier to .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="d1c38-107">Proje Microsoft. AspNetCore. All paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1c38-107">The project uses the Microsoft.AspNetCore.All package.</span></span>

<span data-ttu-id="d1c38-108">`PackageReference`Microsoft. AspNetCore. All için ' i kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d1c38-108">Remove the `PackageReference` for Microsoft.AspNetCore.All.</span></span>  <span data-ttu-id="d1c38-109">Ayrıca, Microsoft. AspNetCore. All 'tan başvurulan ancak ASP.NET Core paylaşılan çerçevesine dahil olmayan paketler için paket başvuruları eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c38-109">You may also need to add package references for packages that were referenced from Microsoft.AspNetCore.All but are not included in the ASP.NET Core shared framework.</span></span>  <span data-ttu-id="d1c38-110">Bu paketler burada listelenmiştir: [Microsoft. AspNetCore. All 'Dan Microsoft. AspNetCore. app 'e geçiş](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="d1c38-110">These packages are listed here: [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span></span>

<span data-ttu-id="d1c38-111">Ayrıca bkz. [ASP.NET Core 2,2 ' den 3,0 ' e geçiş](/aspnet/core/migration/22-to-30)</span><span class="sxs-lookup"><span data-stu-id="d1c38-111">See also [Migrate from ASP.NET Core 2.2 to 3.0](/aspnet/core/migration/22-to-30)</span></span>

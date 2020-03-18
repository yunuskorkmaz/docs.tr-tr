---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179974"
---
> [!NOTE]
> <span data-ttu-id="2f1b6-101">.NET Core 2.0 ile başlayarak, geri [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) yükleme `dotnet build` gibi ve `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="2f1b6-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="2f1b6-102">[Azure DevOps Hizmetleri'ndeki sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya geri yüklemenin gerçekleştiği zamanı açıkça denetlemesi gereken yapı sistemleri gibi açık bir geri yükleme yapmanın mantıklı olduğu belirli senaryolarda yine de geçerli bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="2f1b6-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="2f1b6-103">Bu komut, `dotnet restore` uzun formda geçirildiğinde (örneğin,) `--source`seçenekleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="2f1b6-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="2f1b6-104">Kısa form seçenekleri, `-s`örneğin, desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2f1b6-104">Short form options, such as `-s`, are not supported.</span></span>

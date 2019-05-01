---
ms.openlocfilehash: 95fd83d517096eecb69e57f15c8c70f497a290b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646949"
---
> [!NOTE]
> <span data-ttu-id="c82b5-101">.NET Core 2.0 SDK'sı ile başlayarak, çalıştırma gerekmez [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) bir geri yükleme, örneğin, gerçekleşmesi için gerekli tüm komutlar tarafından örtük olarak çalıştırıldığından `dotnet new`, `dotnet build` ve `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="c82b5-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="c82b5-102">Bunu hala geçerli bir komut burada açık bir geri yükleme yaparsanız anlamlı, bazı senaryolarda olduğu gibi [sürekli tümleştirme derlemeleri Azure DevOps Hizmetleri'nde](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya açıkça zaman denetlemek için gereken derleme sistemlerinde geri yükleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c82b5-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
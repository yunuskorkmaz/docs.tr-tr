---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632101"
---
> [!NOTE]
> <span data-ttu-id="38450-101">.NET Core 2.0 SDK ile başlayarak, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) geri yükleme nin gerçekleşmesini gerektiren tüm komutlar tarafından örtülü `dotnet new`olarak `dotnet build` `dotnet run`çalıştırıldığı için çalıştırmak zorunda değilsiniz, ve .</span><span class="sxs-lookup"><span data-stu-id="38450-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="38450-102">[Azure DevOps Hizmetleri'ndeki sürekli tümleştirme yapıları](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya geri yüklemenin gerçekleştiği zamanı açıkça denetlemesi gereken yapı sistemleri gibi açık bir geri yükleme yapmanın mantıklı olduğu belirli senaryolarda yine de geçerli bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="38450-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>

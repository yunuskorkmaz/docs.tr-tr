---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179974"
---
> [!NOTE]
> <span data-ttu-id="8149b-101">.NET Core 2,0 ' den başlayarak [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ' i çalıştırmanız gerekmez, çünkü `dotnet build` ve `dotnet run` gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8149b-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="8149b-102">Bir açık geri yüklemeyi yapmanın, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yükleme işleminin gerçekleştiği süreyi açıkça denetması gereken belirli senaryolarda geçerli bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="8149b-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="8149b-103">Bu komut, uzun biçimde geçirildiğinde `dotnet restore` seçeneklerini de destekler (örneğin, `--source`).</span><span class="sxs-lookup"><span data-stu-id="8149b-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="8149b-104">@No__t-0 gibi kısa form seçenekleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8149b-104">Short form options, such as `-s`, are not supported.</span></span>

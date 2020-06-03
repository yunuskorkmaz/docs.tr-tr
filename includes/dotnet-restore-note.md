---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102754"
---
<span data-ttu-id="274a4-101">,,,, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) Ve gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırıldığı için çalıştırmanız gerekmez `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="274a4-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="274a4-102">Örtük geri yüklemeyi devre dışı bırakmak için `--no-restore` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="274a4-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="274a4-103">`dotnet restore`Bu komut, açıkça geri yükleme işleminin, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yüklemenin ne zaman gerçekleşeceğini açıkça denetmasının gerektiği bazı senaryolarda de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="274a4-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="274a4-104">NuGet beslemelerini yönetme hakkında daha fazla bilgi için [ `dotnet restore` belgelerine](../docs/core/tools/dotnet-restore.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="274a4-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>

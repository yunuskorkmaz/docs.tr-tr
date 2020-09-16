---
ms.openlocfilehash: 19002cce40fdc929716a761a5e01303be4decb35
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537840"
---
<span data-ttu-id="554c0-101">,,,, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) Ve gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırıldığı için çalıştırmanız gerekmez `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="554c0-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="554c0-102">Örtük geri yüklemeyi devre dışı bırakmak için `--no-restore` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="554c0-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="554c0-103">`dotnet restore`Bu komut, açıkça geri yükleme işleminin, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yüklemenin ne zaman gerçekleşeceğini açıkça denetmasının gerektiği bazı senaryolarda de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="554c0-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="554c0-104">NuGet beslemelerini yönetme hakkında daha fazla bilgi için [ `dotnet restore` belgelerine](../docs/core/tools/dotnet-restore.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="554c0-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>

<span data-ttu-id="554c0-105">Bu komut, `dotnet restore` uzun biçimde geçirildiğinde seçenekleri destekler (örneğin, `--source` ).</span><span class="sxs-lookup"><span data-stu-id="554c0-105">This command supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="554c0-106">Gibi kısa form seçenekleri `-s` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="554c0-106">Short form options, such as `-s`, are not supported.</span></span>

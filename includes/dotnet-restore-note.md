---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102754"
---
<span data-ttu-id="0549a-101">Geri yükleme yapılmasını gerektiren [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) tüm komutlar tarafından örtülü olarak çalıştırıldığı için çalıştırmak zorunda `dotnet new` `dotnet build`değilsiniz, `dotnet publish`, `dotnet pack`, `dotnet run` `dotnet test`, , ve .</span><span class="sxs-lookup"><span data-stu-id="0549a-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="0549a-102">Örtülü geri yüklemeyi devre `--no-restore` dışı kalmak için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="0549a-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="0549a-103">Komut, `dotnet restore` [Azure DevOps Hizmetleri'ndeki sürekli tümleştirme yapıları](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya geri yükleme nin ne zaman gerçekleşacağını açıkça denetlemesi gereken yapı sistemleri gibi açıkça geri yüklemenin mantıklı olduğu belirli senaryolarda yine de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0549a-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="0549a-104">NuGet akışlarının nasıl yönetilenhakkında bilgi için [ `dotnet restore` belgelere](../docs/core/tools/dotnet-restore.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0549a-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>

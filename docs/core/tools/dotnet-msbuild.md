---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733199"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="db1e7-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="db1e7-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="db1e7-104">Ad</span><span class="sxs-lookup"><span data-stu-id="db1e7-104">Name</span></span>

<span data-ttu-id="db1e7-105">`dotnet msbuild`-bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db1e7-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db1e7-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="db1e7-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="db1e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db1e7-107">Description</span></span>

<span data-ttu-id="db1e7-108">`dotnet msbuild` komutu, tam işlevli MSBuild 'e erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1e7-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="db1e7-109">Komutu, yalnızca SDK stilindeki projeler için mevcut MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db1e7-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="db1e7-110">Seçenekler aynı.</span><span class="sxs-lookup"><span data-stu-id="db1e7-110">The options are all the same.</span></span> <span data-ttu-id="db1e7-111">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="db1e7-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="db1e7-112">[DotNet derleme](dotnet-build.md) komutu `dotnet msbuild -restore -target:Build`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="db1e7-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="db1e7-113">[DotNet derlemesi](dotnet-build.md) , proje oluşturmak için daha yaygın olarak kullanılır, ancak her zaman derleme hedefini çalıştırdığı için, projeyi derlemek istemediğinizde `dotnet msbuild` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1e7-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="db1e7-114">Örneğin, projeyi oluşturmadan çalıştırmak istediğiniz belirli bir hedef varsa `dotnet msbuild` kullanın ve hedefi belirtin.</span><span class="sxs-lookup"><span data-stu-id="db1e7-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="db1e7-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="db1e7-115">Examples</span></span>

* <span data-ttu-id="db1e7-116">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db1e7-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="db1e7-117">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db1e7-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="db1e7-118">Yayımla hedefini çalıştırın ve RID `osx.10.11-x64` için yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="db1e7-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="db1e7-119">SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="db1e7-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```

---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503668"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="40273-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="40273-103">dotnet msbuild</span></span>

<span data-ttu-id="40273-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="40273-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="40273-105">Adı</span><span class="sxs-lookup"><span data-stu-id="40273-105">Name</span></span>

<span data-ttu-id="40273-106">`dotnet msbuild`-bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40273-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40273-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="40273-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="40273-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40273-108">Description</span></span>

<span data-ttu-id="40273-109">`dotnet msbuild` komutu, tam işlevli MSBuild 'e erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="40273-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="40273-110">Komutu, yalnızca SDK stilindeki projeler için mevcut MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="40273-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="40273-111">Seçenekler aynı.</span><span class="sxs-lookup"><span data-stu-id="40273-111">The options are all the same.</span></span> <span data-ttu-id="40273-112">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="40273-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="40273-113">[DotNet derleme](dotnet-build.md) komutu `dotnet msbuild -restore -target:Build`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="40273-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="40273-114">[DotNet derlemesi](dotnet-build.md) , proje oluşturmak için daha yaygın olarak kullanılır, ancak her zaman derleme hedefini çalıştırdığı için, projeyi derlemek istemediğinizde `dotnet msbuild` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40273-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="40273-115">Örneğin, projeyi oluşturmadan çalıştırmak istediğiniz belirli bir hedef varsa `dotnet msbuild` kullanın ve hedefi belirtin.</span><span class="sxs-lookup"><span data-stu-id="40273-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="40273-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="40273-116">Examples</span></span>

- <span data-ttu-id="40273-117">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="40273-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="40273-118">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="40273-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="40273-119">Yayımla hedefini çalıştırın ve RID `osx.10.11-x64` için yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="40273-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="40273-120">SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="40273-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```

---
title: dotnet msbuild komutu
description: dotnet msbuild komutu MSBuild komut satırına erişim sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463621"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="9c9e6-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9c9e6-103">dotnet msbuild</span></span>

<span data-ttu-id="9c9e6-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="9c9e6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9c9e6-105">Adı</span><span class="sxs-lookup"><span data-stu-id="9c9e6-105">Name</span></span>

<span data-ttu-id="9c9e6-106">`dotnet msbuild`- Bir proje ve tüm bağımlılıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9c9e6-107">Özet</span><span class="sxs-lookup"><span data-stu-id="9c9e6-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="9c9e6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c9e6-108">Description</span></span>

<span data-ttu-id="9c9e6-109">Komut, `dotnet msbuild` tamamen işlevsel bir MSBuild erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="9c9e6-110">Komut, yalnızca SDK tarzı projeler için varolan MSBuild komut satırı istemcisi ile aynı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="9c9e6-111">Seçeneklerin hepsi aynı.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-111">The options are all the same.</span></span> <span data-ttu-id="9c9e6-112">Kullanılabilir seçenekler hakkında daha fazla bilgi için [MSBuild komut satırı başvurusuna](/visualstudio/msbuild/msbuild-command-line-reference)bakın.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="9c9e6-113">[Dotnet yapı](dotnet-build.md) komutu `dotnet msbuild -restore -target:Build`' ya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="9c9e6-114">[dotnet yapı](dotnet-build.md) daha yaygın olarak proje oluşturmak için kullanılır, ancak her `dotnet msbuild` zaman yapı hedefini çalıştırdığından, projeyi oluşturmak istemediğinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="9c9e6-115">Örneğin, projeyi oluşturmadan çalıştırmak istediğiniz belirli bir hedefiniz `dotnet msbuild` varsa, hedefi kullanın ve belirtin.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="9c9e6-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9c9e6-116">Examples</span></span>

- <span data-ttu-id="9c9e6-117">Bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="9c9e6-118">Sürüm yapılandırmasını kullanarak bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="9c9e6-119">Yayımlama hedefini çalıştırın `osx.10.11-x64` ve RID için yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="9c9e6-120">SDK tarafından dahil edilen tüm hedeflerle tüm projeyi görün:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```

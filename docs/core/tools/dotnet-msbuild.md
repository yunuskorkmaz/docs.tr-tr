---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803168"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="d94a5-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d94a5-103">dotnet msbuild</span></span>

<span data-ttu-id="d94a5-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d94a5-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d94a5-105">Name</span><span class="sxs-lookup"><span data-stu-id="d94a5-105">Name</span></span>

<span data-ttu-id="d94a5-106">`dotnet msbuild`-Bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d94a5-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="d94a5-107">Note: birden çok varsa bir çözüm veya proje dosyasının belirtilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d94a5-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d94a5-108">Özeti</span><span class="sxs-lookup"><span data-stu-id="d94a5-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="d94a5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d94a5-109">Description</span></span>

<span data-ttu-id="d94a5-110">`dotnet msbuild`Komut, tam Işlevli MSBuild 'e erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d94a5-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="d94a5-111">Komutu, yalnızca SDK stilindeki projeler için mevcut MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d94a5-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="d94a5-112">Seçenekler aynı.</span><span class="sxs-lookup"><span data-stu-id="d94a5-112">The options are all the same.</span></span> <span data-ttu-id="d94a5-113">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d94a5-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="d94a5-114">[DotNet derleme](dotnet-build.md) komutu ile eşdeğerdir `dotnet msbuild -restore` .</span><span class="sxs-lookup"><span data-stu-id="d94a5-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="d94a5-115">Projeyi derlemek istemediğinizde ve çalıştırmak istediğiniz belirli bir hedef varsa, veya öğesini kullanın `dotnet build` `dotnet msbuild` ve hedefi belirtin.</span><span class="sxs-lookup"><span data-stu-id="d94a5-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="d94a5-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d94a5-116">Examples</span></span>

- <span data-ttu-id="d94a5-117">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d94a5-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="d94a5-118">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d94a5-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="d94a5-119">Yayımla hedefini çalıştırın ve RID için yayımlayın `osx.10.11-x64` :</span><span class="sxs-lookup"><span data-stu-id="d94a5-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="d94a5-120">SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="d94a5-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```

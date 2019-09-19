---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117697"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="cb485-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="cb485-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cb485-104">Ad</span><span class="sxs-lookup"><span data-stu-id="cb485-104">Name</span></span>

<span data-ttu-id="cb485-105">`dotnet msbuild`-Bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb485-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb485-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="cb485-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="cb485-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb485-107">Description</span></span>

<span data-ttu-id="cb485-108">Komut `dotnet msbuild` , tam işlevli MSBuild 'e erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb485-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="cb485-109">Komutu, yalnızca SDK stili proje için mevcut olan MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cb485-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="cb485-110">Seçenekler aynı.</span><span class="sxs-lookup"><span data-stu-id="cb485-110">The options are all the same.</span></span> <span data-ttu-id="cb485-111">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="cb485-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="cb485-112">[DotNet derleme](dotnet-build.md) komutu ile `dotnet msbuild -restore -target:Build`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cb485-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="cb485-113">`dotnet build`, proje oluşturmak için daha yaygın olarak kullanılır, `dotnet msbuild` ancak size daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb485-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="cb485-114">Örneğin, çalıştırmak istediğiniz belirli bir hedef varsa (derleme hedefini çalıştırmadan) muhtemelen kullanmak `dotnet msbuild`istersiniz.</span><span class="sxs-lookup"><span data-stu-id="cb485-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="cb485-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cb485-115">Examples</span></span>

* <span data-ttu-id="cb485-116">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cb485-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="cb485-117">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cb485-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="cb485-118">Yayımla hedefini çalıştırın ve `osx.10.11-x64` RID için yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="cb485-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="cb485-119">SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="cb485-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```

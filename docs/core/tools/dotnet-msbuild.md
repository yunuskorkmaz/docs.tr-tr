---
title: DotNet msbuild komut
description: Dotnet msbuild komut MSBuild komut satırını erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: f025b5b92e57c7b804b9bdd59c8b4a4a806796da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648704"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="579cd-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="579cd-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="579cd-104">Ad</span><span class="sxs-lookup"><span data-stu-id="579cd-104">Name</span></span>

<span data-ttu-id="579cd-105">`dotnet msbuild` -Bir proje ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="579cd-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="579cd-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="579cd-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="579cd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579cd-107">Description</span></span>

<span data-ttu-id="579cd-108">`dotnet msbuild` Komutu tam olarak işlevsel bir MSBuild erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="579cd-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="579cd-109">Komutu yalnızca SDK stilinde proje var olan MSBuild komut satırı istemcisi tam aynı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="579cd-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="579cd-110">Seçenekler tüm aynıdır.</span><span class="sxs-lookup"><span data-stu-id="579cd-110">The options are all the same.</span></span> <span data-ttu-id="579cd-111">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="579cd-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="579cd-112">[Dotnet derleme](dotnet-build.md) komutu için eşdeğer `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="579cd-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="579cd-113">`dotnet build` projeleri oluşturmak için daha yaygın olarak kullanılır, ancak `dotnet msbuild` daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="579cd-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="579cd-114">(Çalışan yapı hedefi olmadan) çalıştırmak istediğiniz belirli bir hedef varsa, örneğin, büyük olasılıkla kullanmak istediğiniz `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="579cd-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="579cd-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="579cd-115">Examples</span></span>

* <span data-ttu-id="579cd-116">Bir proje ve bağımlılıkları derleme:</span><span class="sxs-lookup"><span data-stu-id="579cd-116">Build a project and its dependencies:</span></span>

  ```console
  dotnet msbuild
  ```

* <span data-ttu-id="579cd-117">Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="579cd-117">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="579cd-118">Yayımlama hedefi çalıştırın ve yayımlama için `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="579cd-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="579cd-119">SDK tarafından eklenen tüm hedefleri ile tüm proje bakın:</span><span class="sxs-lookup"><span data-stu-id="579cd-119">See the whole project with all targets included by the SDK:</span></span>

  ```console
  dotnet msbuild -pp
  ```
---
title: DotNet msbuild command - .NET Core CLI
description: Dotnet msbuild komut MSBuild komut satırını erişim sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583730"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="43cd8-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="43cd8-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="43cd8-104">Ad</span><span class="sxs-lookup"><span data-stu-id="43cd8-104">Name</span></span>

<span data-ttu-id="43cd8-105">`dotnet msbuild` -Bir proje ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43cd8-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="43cd8-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="43cd8-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="43cd8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43cd8-107">Description</span></span>

<span data-ttu-id="43cd8-108">`dotnet msbuild` Komutu tam olarak işlevsel bir MSBuild erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="43cd8-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="43cd8-109">Komutu, var olan MSBuild komut satırı istemcisi tam aynı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="43cd8-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="43cd8-110">Seçenekler tüm aynıdır.</span><span class="sxs-lookup"><span data-stu-id="43cd8-110">The options are all the same.</span></span> <span data-ttu-id="43cd8-111">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="43cd8-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="43cd8-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="43cd8-112">Examples</span></span>

<span data-ttu-id="43cd8-113">Bir proje ve bağımlılıkları derleme:</span><span class="sxs-lookup"><span data-stu-id="43cd8-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="43cd8-114">Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="43cd8-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild -p:Configuration=Release`

<span data-ttu-id="43cd8-115">Yayımlama hedefi çalıştırın ve yayımlama için `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="43cd8-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="43cd8-116">SDK tarafından eklenen tüm hedefleri ile tüm proje bakın:</span><span class="sxs-lookup"><span data-stu-id="43cd8-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild -pp`

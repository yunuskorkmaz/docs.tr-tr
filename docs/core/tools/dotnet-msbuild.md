---
title: DotNet msbuild komut - .NET Core CLI
description: Dotnet msbuild komut MSBuild komut satırında erişim sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696851"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="bab68-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="bab68-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="bab68-104">Ad</span><span class="sxs-lookup"><span data-stu-id="bab68-104">Name</span></span>

<span data-ttu-id="bab68-105">`dotnet msbuild` -Bir proje ve tüm bağımlılıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bab68-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bab68-106">Özet</span><span class="sxs-lookup"><span data-stu-id="bab68-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="bab68-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bab68-107">Description</span></span>

<span data-ttu-id="bab68-108">`dotnet msbuild` Komutu tam olarak işlevsel MSBuild erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bab68-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="bab68-109">Komut varolan MSBuild komut satırı istemcisi tam aynı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bab68-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="bab68-110">Tümü aynı seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="bab68-110">The options are all the same.</span></span> <span data-ttu-id="bab68-111">Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz: [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="bab68-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="bab68-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bab68-112">Examples</span></span>

<span data-ttu-id="bab68-113">Proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bab68-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="bab68-114">Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bab68-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="bab68-115">Yayımlama hedefi çalıştırın ve için Yayımlama `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="bab68-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="bab68-116">SDK tarafından eklenen tüm hedefleri olan tüm proje bakın:</span><span class="sxs-lookup"><span data-stu-id="bab68-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`

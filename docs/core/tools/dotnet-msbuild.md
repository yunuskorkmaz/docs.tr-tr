---
title: DotNet msbuild komut - .NET Core CLI
description: Dotnet msbuild komut MSBuild komut satırında erişim sağlar.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 9e6f8b3063b4cd2a3a36cae8839d6f83e0466e03
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="14e54-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="14e54-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="14e54-104">Ad</span><span class="sxs-lookup"><span data-stu-id="14e54-104">Name</span></span>

<span data-ttu-id="14e54-105">`dotnet msbuild` -Bir proje ve tüm bağımlılıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14e54-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="14e54-106">Özet</span><span class="sxs-lookup"><span data-stu-id="14e54-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="14e54-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14e54-107">Description</span></span>

<span data-ttu-id="14e54-108">`dotnet msbuild` Komutu tam olarak işlevsel MSBuild erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="14e54-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="14e54-109">Komut varolan MSBuild komut satırı istemcisi tam aynı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="14e54-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="14e54-110">Tümü aynı seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="14e54-110">The options are all the same.</span></span> <span data-ttu-id="14e54-111">Kullanım [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) kullanılabilir seçenekler hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="14e54-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="14e54-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="14e54-112">Examples</span></span>

<span data-ttu-id="14e54-113">Proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="14e54-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="14e54-114">Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="14e54-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="14e54-115">Yayımlama hedefi çalıştırın ve için Yayımlama `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="14e54-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="14e54-116">SDK tarafından eklenen tüm hedefleri olan tüm proje bakın:</span><span class="sxs-lookup"><span data-stu-id="14e54-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`

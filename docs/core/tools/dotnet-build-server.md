---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734381"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="cd951-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="cd951-103">dotnet build-server</span></span>

<span data-ttu-id="cd951-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd951-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="cd951-105">Name</span><span class="sxs-lookup"><span data-stu-id="cd951-105">Name</span></span>

<span data-ttu-id="cd951-106">`dotnet build-server`-bir derleme tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="cd951-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd951-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="cd951-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="cd951-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="cd951-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="cd951-109">DotNet 'ten başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="cd951-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="cd951-110">Varsayılan olarak, tüm sunucular kapanır.</span><span class="sxs-lookup"><span data-stu-id="cd951-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="cd951-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cd951-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="cd951-112">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cd951-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="cd951-113">MSBuild yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="cd951-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="cd951-114">Razor derleme sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="cd951-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="cd951-115">VB/C# derleyici yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="cd951-115">Shuts down the VB/C# compiler build server.</span></span>

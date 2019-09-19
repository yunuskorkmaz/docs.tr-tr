---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117768"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="aa2d8-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="aa2d8-103">dotnet build-server</span></span>

<span data-ttu-id="aa2d8-104">**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="aa2d8-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="aa2d8-105">Ad</span><span class="sxs-lookup"><span data-stu-id="aa2d8-105">Name</span></span>

<span data-ttu-id="aa2d8-106">`dotnet build-server`-Bir derleme tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aa2d8-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="aa2d8-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="aa2d8-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="aa2d8-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="aa2d8-109">DotNet 'ten başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="aa2d8-110">Varsayılan olarak, tüm sunucular kapanır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="aa2d8-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="aa2d8-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="aa2d8-112">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="aa2d8-113">MSBuild yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="aa2d8-114">Razor derleme sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="aa2d8-115">VB/C# derleyici yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="aa2d8-115">Shuts down the VB/C# compiler build server.</span></span>

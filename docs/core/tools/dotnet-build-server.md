---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: b2dfd5f317466f18d9246bd1fb281a92c42f6d9d
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168105"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="73e76-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="73e76-103">dotnet build-server</span></span>

<span data-ttu-id="73e76-104">**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="73e76-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="73e76-105">Ad</span><span class="sxs-lookup"><span data-stu-id="73e76-105">Name</span></span>

<span data-ttu-id="73e76-106">`dotnet build-server`-Bir derleme tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="73e76-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="73e76-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="73e76-107">Synopsis</span></span>

```console
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="73e76-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="73e76-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="73e76-109">DotNet 'ten başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="73e76-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="73e76-110">Varsayılan olarak, tüm sunucular kapanır.</span><span class="sxs-lookup"><span data-stu-id="73e76-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="73e76-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="73e76-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="73e76-112">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="73e76-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="73e76-113">MSBuild yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="73e76-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="73e76-114">Razor derleme sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="73e76-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="73e76-115">VB/C# derleyici yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="73e76-115">Shuts down the VB/C# compiler build server.</span></span>

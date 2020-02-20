---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503784"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="107c6-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="107c6-103">dotnet build-server</span></span>

<span data-ttu-id="107c6-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="107c6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="107c6-105">Adı</span><span class="sxs-lookup"><span data-stu-id="107c6-105">Name</span></span>

<span data-ttu-id="107c6-106">`dotnet build-server`-bir derleme tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="107c6-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="107c6-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="107c6-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="107c6-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="107c6-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="107c6-109">DotNet 'ten başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="107c6-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="107c6-110">Varsayılan olarak, tüm sunucular kapanır.</span><span class="sxs-lookup"><span data-stu-id="107c6-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="107c6-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="107c6-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="107c6-112">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="107c6-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="107c6-113">MSBuild yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="107c6-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="107c6-114">Razor derleme sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="107c6-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="107c6-115">VB/C# derleyici yapı sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="107c6-115">Shuts down the VB/C# compiler build server.</span></span>

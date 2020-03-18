---
title: dotnet build-server komutu
description: Dotnet build-server komutu, bir yapı tarafından başlatılan sunucularla etkileşime girerek etkileşime girer.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503784"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="47a71-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="47a71-103">dotnet build-server</span></span>

<span data-ttu-id="47a71-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="47a71-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="47a71-105">Adı</span><span class="sxs-lookup"><span data-stu-id="47a71-105">Name</span></span>

<span data-ttu-id="47a71-106">`dotnet build-server`- Bir yapı tarafından başlatılan sunucularla etkileşime girerek.</span><span class="sxs-lookup"><span data-stu-id="47a71-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="47a71-107">Özet</span><span class="sxs-lookup"><span data-stu-id="47a71-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="47a71-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="47a71-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="47a71-109">Dotnet'ten başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="47a71-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="47a71-110">Varsayılan olarak, tüm sunucular kapatılır.</span><span class="sxs-lookup"><span data-stu-id="47a71-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="47a71-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="47a71-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="47a71-112">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="47a71-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="47a71-113">MSBuild build sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="47a71-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="47a71-114">Razor build sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="47a71-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="47a71-115">VB/C# derleyici derleme sunucusunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="47a71-115">Shuts down the VB/C# compiler build server.</span></span>

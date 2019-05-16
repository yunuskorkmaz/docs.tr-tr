---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632093"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="da978-103">DotNet yapı sunucu</span><span class="sxs-lookup"><span data-stu-id="da978-103">dotnet build-server</span></span>

<span data-ttu-id="da978-104">**Bu makale için geçerlidir: ✓** .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="da978-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="da978-105">Ad</span><span class="sxs-lookup"><span data-stu-id="da978-105">Name</span></span>

<span data-ttu-id="da978-106">`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="da978-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="da978-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="da978-107">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="da978-108">Komutlar</span><span class="sxs-lookup"><span data-stu-id="da978-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="da978-109">Dotnet başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="da978-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="da978-110">Varsayılan olarak, tüm sunucuların kapatılır.</span><span class="sxs-lookup"><span data-stu-id="da978-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="da978-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="da978-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="da978-112">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="da978-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="da978-113">Yapı sunucusunda MSBuild kapatır.</span><span class="sxs-lookup"><span data-stu-id="da978-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="da978-114">Yapı sunucusunda Razor kapatır.</span><span class="sxs-lookup"><span data-stu-id="da978-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="da978-115">Kapatan VB / C# Derleyici sunucusu derleme.</span><span class="sxs-lookup"><span data-stu-id="da978-115">Shuts down the VB/C# compiler build server.</span></span>

---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169670"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="40d26-103">DotNet yapı sunucu</span><span class="sxs-lookup"><span data-stu-id="40d26-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="40d26-104">Ad</span><span class="sxs-lookup"><span data-stu-id="40d26-104">Name</span></span>

<span data-ttu-id="40d26-105">`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="40d26-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40d26-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="40d26-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="40d26-107">Komutlar</span><span class="sxs-lookup"><span data-stu-id="40d26-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="40d26-108">Dotnet başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="40d26-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="40d26-109">Varsayılan olarak, tüm sunucuların kapatılır.</span><span class="sxs-lookup"><span data-stu-id="40d26-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="40d26-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="40d26-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="40d26-111">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="40d26-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="40d26-112">Yapı sunucusunda MSBuild kapatır.</span><span class="sxs-lookup"><span data-stu-id="40d26-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="40d26-113">Yapı sunucusunda Razor kapatır.</span><span class="sxs-lookup"><span data-stu-id="40d26-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="40d26-114">Kapatan VB / C# Derleyici sunucusu derleme.</span><span class="sxs-lookup"><span data-stu-id="40d26-114">Shuts down the VB/C# compiler build server.</span></span>
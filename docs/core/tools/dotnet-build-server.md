---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665318"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="9a332-103">DotNet yapı sunucu</span><span class="sxs-lookup"><span data-stu-id="9a332-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="9a332-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9a332-104">Name</span></span>

<span data-ttu-id="9a332-105">`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="9a332-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a332-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9a332-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="9a332-107">Komutlar</span><span class="sxs-lookup"><span data-stu-id="9a332-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="9a332-108">Dotnet başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="9a332-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="9a332-109">Varsayılan olarak, tüm sunucuların kapatılır.</span><span class="sxs-lookup"><span data-stu-id="9a332-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="9a332-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9a332-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="9a332-111">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9a332-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="9a332-112">Yapı sunucusunda MSBuild kapatır.</span><span class="sxs-lookup"><span data-stu-id="9a332-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="9a332-113">Yapı sunucusunda Razor kapatır.</span><span class="sxs-lookup"><span data-stu-id="9a332-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="9a332-114">Kapatan VB / C# Derleyici sunucusu derleme.</span><span class="sxs-lookup"><span data-stu-id="9a332-114">Shuts down the VB/C# compiler build server.</span></span>
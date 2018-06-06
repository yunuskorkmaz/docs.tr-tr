---
title: DotNet yapı sunuculu command - .NET Core CLI
description: Dotnet yapı sunuculu bir yapı tarafından başlatılan sunucuları ile etkileşim kurar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696260"
---
# <a name="dotnet-build"></a><span data-ttu-id="65866-103">DotNet derleme</span><span class="sxs-lookup"><span data-stu-id="65866-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="65866-104">Ad</span><span class="sxs-lookup"><span data-stu-id="65866-104">Name</span></span>

<span data-ttu-id="65866-105">`dotnet build-server` -Bir yapı tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="65866-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="65866-106">Özet</span><span class="sxs-lookup"><span data-stu-id="65866-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="65866-107">Komutlar</span><span class="sxs-lookup"><span data-stu-id="65866-107">Commands</span></span>

`shutdown`

<span data-ttu-id="65866-108">Dotnet başlatılan yapı sunucuları kapatır.</span><span class="sxs-lookup"><span data-stu-id="65866-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="65866-109">Varsayılan olarak, tüm sunucuların kapatılır.</span><span class="sxs-lookup"><span data-stu-id="65866-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="65866-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="65866-110">Options</span></span>

`-h|--help`

<span data-ttu-id="65866-111">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="65866-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="65866-112">MSBuild kapatır sunucusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65866-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="65866-113">Razor kapatır sunucusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65866-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="65866-114">VB kapatır / C# Derleyici build sunucu.</span><span class="sxs-lookup"><span data-stu-id="65866-114">Shuts down the VB/C# compiler build server.</span></span>

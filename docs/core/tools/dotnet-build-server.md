---
title: DotNet yapı sunucu command - .NET Core CLI
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404339"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="34ef4-103">DotNet yapı sunucu</span><span class="sxs-lookup"><span data-stu-id="34ef4-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="34ef4-104">Ad</span><span class="sxs-lookup"><span data-stu-id="34ef4-104">Name</span></span>

<span data-ttu-id="34ef4-105">`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="34ef4-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="34ef4-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="34ef4-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="34ef4-107">Komutlar</span><span class="sxs-lookup"><span data-stu-id="34ef4-107">Commands</span></span>

`shutdown`

<span data-ttu-id="34ef4-108">Dotnet başlatılan yapı sunucularını kapatır.</span><span class="sxs-lookup"><span data-stu-id="34ef4-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="34ef4-109">Varsayılan olarak, tüm sunucuların kapatılır.</span><span class="sxs-lookup"><span data-stu-id="34ef4-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="34ef4-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="34ef4-110">Options</span></span>

`-h|--help`

<span data-ttu-id="34ef4-111">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="34ef4-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="34ef4-112">Yapı sunucusunda MSBuild kapatır.</span><span class="sxs-lookup"><span data-stu-id="34ef4-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="34ef4-113">Yapı sunucusunda Razor kapatır.</span><span class="sxs-lookup"><span data-stu-id="34ef4-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="34ef4-114">Kapatan VB / C# Derleyici sunucusu derleme.</span><span class="sxs-lookup"><span data-stu-id="34ef4-114">Shuts down the VB/C# compiler build server.</span></span>

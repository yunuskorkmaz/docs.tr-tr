---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734239"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="b80a0-103">DotNet yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="b80a0-103">dotnet help reference</span></span>

<span data-ttu-id="b80a0-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="b80a0-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="b80a0-105">Name</span><span class="sxs-lookup"><span data-stu-id="b80a0-105">Name</span></span>

<span data-ttu-id="b80a0-106">`dotnet help`-belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="b80a0-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b80a0-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="b80a0-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="b80a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b80a0-108">Description</span></span>

<span data-ttu-id="b80a0-109">`dotnet help` komutu, docs.microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.</span><span class="sxs-lookup"><span data-stu-id="b80a0-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="b80a0-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="b80a0-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="b80a0-111">.NET Core CLI komutunun adı.</span><span class="sxs-lookup"><span data-stu-id="b80a0-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="b80a0-112">Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="b80a0-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="b80a0-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b80a0-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="b80a0-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b80a0-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="b80a0-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b80a0-115">Examples</span></span>

* <span data-ttu-id="b80a0-116">[DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:</span><span class="sxs-lookup"><span data-stu-id="b80a0-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```

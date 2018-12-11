---
title: DotNet Yardım komutu
description: Belirtilen komut için çevrimiçi belgeleri ayrıntılı dotnet help komutunu gösterir.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168964"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="4a010-103">DotNet Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="4a010-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="4a010-104">Ad</span><span class="sxs-lookup"><span data-stu-id="4a010-104">Name</span></span>

<span data-ttu-id="4a010-105">`dotnet help` -Gösterir, belirtilen komut için çevrimiçi belgeleri daha ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="4a010-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a010-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="4a010-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="4a010-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a010-107">Description</span></span>

<span data-ttu-id="4a010-108">`dotnet help` Docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için komut başvuru page up açar.</span><span class="sxs-lookup"><span data-stu-id="4a010-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="4a010-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a010-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="4a010-110">.NET Core CLI komut adı.</span><span class="sxs-lookup"><span data-stu-id="4a010-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="4a010-111">Geçerli CLI komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="4a010-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="4a010-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4a010-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="4a010-113">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4a010-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="4a010-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4a010-114">Examples</span></span>

* <span data-ttu-id="4a010-115">İçin belgeler sayfası açılır [yeni dotnet](dotnet-new.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="4a010-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```
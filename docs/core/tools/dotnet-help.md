---
title: DotNet Yardım komutu
description: Belirtilen komut için çevrimiçi belgeleri ayrıntılı dotnet help komutunu gösterir.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665123"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="8b1fa-103">DotNet Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b1fa-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="8b1fa-104">Ad</span><span class="sxs-lookup"><span data-stu-id="8b1fa-104">Name</span></span>

<span data-ttu-id="8b1fa-105">`dotnet help` -Gösterir, belirtilen komut için çevrimiçi belgeleri daha ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="8b1fa-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b1fa-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8b1fa-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="8b1fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1fa-107">Description</span></span>

<span data-ttu-id="8b1fa-108">`dotnet help` Docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için komut başvuru page up açar.</span><span class="sxs-lookup"><span data-stu-id="8b1fa-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="8b1fa-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b1fa-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="8b1fa-110">.NET Core CLI komut adı.</span><span class="sxs-lookup"><span data-stu-id="8b1fa-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="8b1fa-111">Geçerli CLI komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="8b1fa-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="8b1fa-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8b1fa-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="8b1fa-113">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8b1fa-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="8b1fa-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8b1fa-114">Examples</span></span>

* <span data-ttu-id="8b1fa-115">İçin belgeler sayfası açılır [yeni dotnet](dotnet-new.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="8b1fa-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```
---
title: dotnet yardım komutu
description: Dotnet yardım komutu, belirtilen komut için çevrimiçi olarak daha ayrıntılı belgeler gösterir.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463686"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="ae4e2-103">dotnet yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae4e2-103">dotnet help reference</span></span>

<span data-ttu-id="ae4e2-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="ae4e2-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ae4e2-105">Adı</span><span class="sxs-lookup"><span data-stu-id="ae4e2-105">Name</span></span>

<span data-ttu-id="ae4e2-106">`dotnet help`- Belirtilen komut için daha ayrıntılı belgeleri çevrimiçi olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae4e2-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ae4e2-107">Özet</span><span class="sxs-lookup"><span data-stu-id="ae4e2-107">Synopsis</span></span>

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ae4e2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae4e2-108">Description</span></span>

<span data-ttu-id="ae4e2-109">Komut, `dotnet help` docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için başvuru sayfasını açar.</span><span class="sxs-lookup"><span data-stu-id="ae4e2-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="ae4e2-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ae4e2-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="ae4e2-111">.NET Core CLI komutunun adı.</span><span class="sxs-lookup"><span data-stu-id="ae4e2-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="ae4e2-112">Geçerli CLI komutlarının listesi için [CLI komutlarına](index.md#cli-commands)bakın.</span><span class="sxs-lookup"><span data-stu-id="ae4e2-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="ae4e2-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ae4e2-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="ae4e2-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ae4e2-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ae4e2-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ae4e2-115">Examples</span></span>

- <span data-ttu-id="ae4e2-116">[dotnet yeni](dotnet-new.md) komutu için dokümantasyon sayfasını açar:</span><span class="sxs-lookup"><span data-stu-id="ae4e2-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```

---
title: DotNet aracı Run komutu
description: DotNet aracı Run komutu, yerel bir araç çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543882"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="11a21-103">DotNet aracı çalıştırması</span><span class="sxs-lookup"><span data-stu-id="11a21-103">dotnet tool run</span></span>

<span data-ttu-id="11a21-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="11a21-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="11a21-105">Adı</span><span class="sxs-lookup"><span data-stu-id="11a21-105">Name</span></span>

<span data-ttu-id="11a21-106">`dotnet tool run`-yerel bir araç çağırır.</span><span class="sxs-lookup"><span data-stu-id="11a21-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="11a21-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="11a21-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="11a21-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11a21-108">Description</span></span>

<span data-ttu-id="11a21-109">`dotnet tool run` komutu, geçerli dizinin kapsamındaki araç bildirimi dosyalarını arar.</span><span class="sxs-lookup"><span data-stu-id="11a21-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="11a21-110">Belirtilen araca bir başvuru bulduğunda, aracı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="11a21-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="11a21-111">Daha fazla bilgi için bkz. [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="11a21-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="11a21-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="11a21-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="11a21-113">Çalıştırılacak aracın komut adı.</span><span class="sxs-lookup"><span data-stu-id="11a21-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="11a21-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="11a21-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="11a21-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="11a21-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="11a21-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="11a21-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="11a21-117">`dotnetsay` yerel aracını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="11a21-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="11a21-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a21-118">See also</span></span>

- [<span data-ttu-id="11a21-119">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="11a21-119">.NET Core tools</span></span>](global-tools.md)

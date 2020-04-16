---
title: dotnet aracı çalıştırma komutu
description: Dotnet araç çalıştırma komutu yerel bir aracı çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463322"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="911db-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="911db-103">dotnet tool run</span></span>

<span data-ttu-id="911db-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="911db-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="911db-105">Adı</span><span class="sxs-lookup"><span data-stu-id="911db-105">Name</span></span>

<span data-ttu-id="911db-106">`dotnet tool run`- Yerel bir aracı çağırır.</span><span class="sxs-lookup"><span data-stu-id="911db-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="911db-107">Özet</span><span class="sxs-lookup"><span data-stu-id="911db-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="911db-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="911db-108">Description</span></span>

<span data-ttu-id="911db-109">Komut, `dotnet tool run` geçerli dizinin kapsamı içinde olan araç bildirimi dosyalarını arar.</span><span class="sxs-lookup"><span data-stu-id="911db-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="911db-110">Belirtilen araca bir başvuru bulduğunda, aracı çalıştırZ.</span><span class="sxs-lookup"><span data-stu-id="911db-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="911db-111">Daha fazla bilgi için yerel [bir aracı Çağır'a](global-tools.md#invoke-a-local-tool)bakın.</span><span class="sxs-lookup"><span data-stu-id="911db-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="911db-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="911db-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="911db-113">Çalıştırılabilmek için aracın komut adı.</span><span class="sxs-lookup"><span data-stu-id="911db-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="911db-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="911db-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="911db-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="911db-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="911db-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="911db-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="911db-117">`dotnetsay` Yerel aracı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="911db-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="911db-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="911db-118">See also</span></span>

- [<span data-ttu-id="911db-119">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="911db-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="911db-120">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="911db-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)

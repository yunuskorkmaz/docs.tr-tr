---
title: dotnet aracı çalıştırma komutu
description: Dotnet araç çalıştırma komutu yerel bir aracı çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847852"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="67039-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="67039-103">dotnet tool run</span></span>

<span data-ttu-id="67039-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="67039-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="67039-105">Adı</span><span class="sxs-lookup"><span data-stu-id="67039-105">Name</span></span>

<span data-ttu-id="67039-106">`dotnet tool run`- Yerel bir aracı çağırır.</span><span class="sxs-lookup"><span data-stu-id="67039-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67039-107">Özet</span><span class="sxs-lookup"><span data-stu-id="67039-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="67039-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67039-108">Description</span></span>

<span data-ttu-id="67039-109">Komut, `dotnet tool run` geçerli dizinin kapsamı içinde olan araç bildirimi dosyalarını arar.</span><span class="sxs-lookup"><span data-stu-id="67039-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="67039-110">Belirtilen araca bir başvuru bulduğunda, aracı çalıştırZ.</span><span class="sxs-lookup"><span data-stu-id="67039-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="67039-111">Daha fazla bilgi için yerel [bir aracı Çağır'a](global-tools.md#invoke-a-local-tool)bakın.</span><span class="sxs-lookup"><span data-stu-id="67039-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="67039-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="67039-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="67039-113">Çalıştırılabilmek için aracın komut adı.</span><span class="sxs-lookup"><span data-stu-id="67039-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="67039-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="67039-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="67039-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="67039-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="67039-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="67039-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="67039-117">`dotnetsay` Yerel aracı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67039-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="67039-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67039-118">See also</span></span>

- [<span data-ttu-id="67039-119">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="67039-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="67039-120">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="67039-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)

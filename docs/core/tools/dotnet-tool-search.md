---
title: DotNet aracı arama komutu
description: DotNet aracı arama komutu, NuGet.org 'de yayınlanan .NET araçlarını arar.
ms.date: 11/11/2020
ms.openlocfilehash: e0289e651ec4a439c791c8c948bef2d85d9c3794
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634148"
---
# <a name="dotnet-tool-search"></a><span data-ttu-id="19ef6-103">DotNet aracı araması</span><span class="sxs-lookup"><span data-stu-id="19ef6-103">dotnet tool search</span></span>

<span data-ttu-id="19ef6-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="19ef6-104">**This article applies to:** ✔️ .NET 5.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="19ef6-105">Name</span><span class="sxs-lookup"><span data-stu-id="19ef6-105">Name</span></span>

<span data-ttu-id="19ef6-106">`dotnet tool search` -NuGet 'e yayınlanan tüm [.net araçlarını](global-tools.md) arar.</span><span class="sxs-lookup"><span data-stu-id="19ef6-106">`dotnet tool search` - Searches all [.NET tools](global-tools.md) that are published to NuGet.</span></span>

## <a name="synopsis"></a><span data-ttu-id="19ef6-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="19ef6-107">Synopsis</span></span>

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a><span data-ttu-id="19ef6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19ef6-108">Description</span></span>

<span data-ttu-id="19ef6-109">`dotnet tool search`Komut, .net küresel, araç yolu veya yerel araçlar olarak kullanılabilecek araçlar Için NuGet araması yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="19ef6-109">The `dotnet tool search` command provides a way for you to search NuGet for tools that can be used as .NET global, tool-path, or local tools.</span></span> <span data-ttu-id="19ef6-110">Komut, araç adlarını ve başlıklar, açıklamalar ve Etiketler gibi meta verileri arar.</span><span class="sxs-lookup"><span data-stu-id="19ef6-110">The command searches the tool names and metadata such as titles, descriptions, and tags.</span></span>

<span data-ttu-id="19ef6-111">Komut [NuGet arama API](/nuget/api/search-query-service-resource#search-for-packages)'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="19ef6-111">The command uses the [NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages).</span></span> <span data-ttu-id="19ef6-112">`packageType=dotnettool`Yalnızca .NET araç paketleri seçmek için üzerine filtreler.</span><span class="sxs-lookup"><span data-stu-id="19ef6-112">It filters on `packageType=dotnettool` to select only .NET tool packages.</span></span>

## <a name="options"></a><span data-ttu-id="19ef6-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="19ef6-113">Options</span></span>

- **`--detail`**

  <span data-ttu-id="19ef6-114">Sorgunun ayrıntılı sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19ef6-114">Shows detailed results from the query.</span></span>

- **`--prerelease`**

  <span data-ttu-id="19ef6-115">Yayın öncesi paketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="19ef6-115">Includes pre-release packages.</span></span>

- **`--skip <NUMBER>`**

  <span data-ttu-id="19ef6-116">Atlanacak sorgu sonuçlarının sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19ef6-116">Specifies the number of query results to skip.</span></span> <span data-ttu-id="19ef6-117">Sayfalandırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19ef6-117">Used for pagination.</span></span>

- **`--take <NUMBER>`**

  <span data-ttu-id="19ef6-118">Gösterilecek sorgu sonuçlarının sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19ef6-118">Specifies the number of query results to show.</span></span> <span data-ttu-id="19ef6-119">Sayfalandırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19ef6-119">Used for pagination.</span></span>

- **`-h|--help`**

  <span data-ttu-id="19ef6-120">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19ef6-120">Shows command-line help.</span></span>

## <a name="examples"></a><span data-ttu-id="19ef6-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19ef6-121">Examples</span></span>

- <span data-ttu-id="19ef6-122">Paket adı veya açıklamasında "biçim" içeren .NET araçları için arama NuGet.org:</span><span class="sxs-lookup"><span data-stu-id="19ef6-122">Search NuGet.org for .NET tools that have "format" in their package name or description:</span></span>

  ```dotnetcli
  dotnet tool search format
  ```

  <span data-ttu-id="19ef6-123">Çıktı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="19ef6-123">The output looks like the following example:</span></span>

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- <span data-ttu-id="19ef6-124">Paket adı veya meta verilerinde "biçim" olan .NET araçları için arama yapın, yalnızca ilk sonucu gösterin ve ayrıntılı bir görünüm görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="19ef6-124">Search NuGet.org for .NET tools that have "format" in their package name or metadata, show only the first result, and show a detailed view.</span></span>

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  <span data-ttu-id="19ef6-125">Çıktı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="19ef6-125">The output looks like the following example:</span></span>

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a><span data-ttu-id="19ef6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19ef6-126">See also</span></span>

- [<span data-ttu-id="19ef6-127">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="19ef6-127">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="19ef6-128">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="19ef6-128">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="19ef6-129">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="19ef6-129">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)

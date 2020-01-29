---
title: DotNet başvuru komutu Ekle
description: DotNet başvuru komutu, proje başvurularına proje eklemek için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: dc8bc01a2bff4f2cf3a8af9efb233448d7de337f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733277"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="cec56-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="cec56-103">dotnet add reference</span></span>

<span data-ttu-id="cec56-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="cec56-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="cec56-105">Name</span><span class="sxs-lookup"><span data-stu-id="cec56-105">Name</span></span>

<span data-ttu-id="cec56-106">`dotnet add reference`-projeden projeye (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="cec56-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cec56-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="cec56-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="cec56-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cec56-108">Description</span></span>

<span data-ttu-id="cec56-109">`dotnet add reference` komutu bir projeye proje başvuruları eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cec56-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="cec56-110">Komutu çalıştırdıktan sonra, `<ProjectReference>` öğeleri proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="cec56-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="cec56-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="cec56-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="cec56-112">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cec56-112">Specifies the project file.</span></span> <span data-ttu-id="cec56-113">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="cec56-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="cec56-114">Eklenecek projeden projeye (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="cec56-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="cec56-115">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="cec56-115">Specify one or more projects.</span></span> <span data-ttu-id="cec56-116">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cec56-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="cec56-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cec56-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="cec56-118">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cec56-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="cec56-119">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken proje başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="cec56-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="cec56-120">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="cec56-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="cec56-121">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cec56-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="cec56-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cec56-122">Examples</span></span>

- <span data-ttu-id="cec56-123">Proje başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="cec56-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="cec56-124">Geçerli dizindeki projeye birden çok proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cec56-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="cec56-125">Linux/Unix üzerinde glob bir model kullanarak birden çok proje başvurusu ekleme:</span><span class="sxs-lookup"><span data-stu-id="cec56-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```

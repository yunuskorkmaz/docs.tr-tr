---
title: DotNet-başvuru komutu Ekle
description: DotNet başvuru komutu, proje başvurularına proje eklemek için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784053"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="5796b-103">DotNet-başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="5796b-103">dotnet-add reference</span></span>

<span data-ttu-id="5796b-104">**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5796b-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5796b-105">Ad</span><span class="sxs-lookup"><span data-stu-id="5796b-105">Name</span></span>

<span data-ttu-id="5796b-106">`dotnet add reference`-Projeden projeye (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="5796b-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5796b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5796b-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="5796b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5796b-108">Description</span></span>

<span data-ttu-id="5796b-109">Komut `dotnet add reference` , projeye proje başvuruları eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5796b-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="5796b-110">Komutu çalıştırdıktan sonra `<ProjectReference>` öğeler proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="5796b-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="5796b-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="5796b-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="5796b-112">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5796b-112">Specifies the project file.</span></span> <span data-ttu-id="5796b-113">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5796b-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="5796b-114">Eklenecek projeden projeye (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="5796b-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="5796b-115">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="5796b-115">Specify one or more projects.</span></span> <span data-ttu-id="5796b-116">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5796b-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="5796b-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5796b-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="5796b-118">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5796b-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5796b-119">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken proje başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="5796b-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`--interactive`**

  <span data-ttu-id="5796b-120">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="5796b-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="5796b-121">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5796b-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="5796b-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5796b-122">Examples</span></span>

* <span data-ttu-id="5796b-123">Proje başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="5796b-123">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="5796b-124">Geçerli dizindeki projeye birden çok proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5796b-124">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="5796b-125">Linux/Unix üzerinde glob bir model kullanarak birden çok proje başvurusu ekleme:</span><span class="sxs-lookup"><span data-stu-id="5796b-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```

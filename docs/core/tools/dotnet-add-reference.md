---
title: dotnet referans komutu ekleyin
description: Dotnet add reference komutu proje başvurularına proje eklemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: f2bd67d181784c4858b8971d05053d196df7818e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463741"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="babb4-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="babb4-103">dotnet add reference</span></span>

<span data-ttu-id="babb4-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="babb4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="babb4-105">Adı</span><span class="sxs-lookup"><span data-stu-id="babb4-105">Name</span></span>

<span data-ttu-id="babb4-106">`dotnet add reference`- Projeden projeye (P2P) başvurular ekler.</span><span class="sxs-lookup"><span data-stu-id="babb4-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="babb4-107">Özet</span><span class="sxs-lookup"><span data-stu-id="babb4-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="babb4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="babb4-108">Description</span></span>

<span data-ttu-id="babb4-109">Komut, `dotnet add reference` projeye proje başvuruları eklemek için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="babb4-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="babb4-110">Komutu çalıştırdıktan `<ProjectReference>` sonra, öğeler proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="babb4-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="babb4-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="babb4-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="babb4-112">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="babb4-112">Specifies the project file.</span></span> <span data-ttu-id="babb4-113">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="babb4-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="babb4-114">Projeden projeye (P2P) başvurular eklemek.</span><span class="sxs-lookup"><span data-stu-id="babb4-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="babb4-115">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="babb4-115">Specify one or more projects.</span></span> <span data-ttu-id="babb4-116">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) Unix/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="babb4-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="babb4-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="babb4-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="babb4-118">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken proje referansları ekler.</span><span class="sxs-lookup"><span data-stu-id="babb4-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="babb4-119">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="babb4-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="babb4-120">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="babb4-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="babb4-121">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="babb4-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="babb4-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="babb4-122">Examples</span></span>

- <span data-ttu-id="babb4-123">Proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="babb4-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="babb4-124">Geçerli dizinde projeye birden çok proje referansı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="babb4-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="babb4-125">Linux/Unix üzerinde globbing deseni kullanarak birden çok proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="babb4-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```

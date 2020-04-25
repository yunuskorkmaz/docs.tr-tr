---
title: DotNet başvuru komutu Ekle
description: DotNet başvuru komutu, proje başvurularına proje eklemek için uygun bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b261e24ed6a9d5bd489d317d2663b1420b5c34ff
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158326"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="90b8e-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="90b8e-103">dotnet add reference</span></span>

<span data-ttu-id="90b8e-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="90b8e-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="90b8e-105">Adı</span><span class="sxs-lookup"><span data-stu-id="90b8e-105">Name</span></span>

<span data-ttu-id="90b8e-106">`dotnet add reference`-Projeden projeye (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="90b8e-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="90b8e-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="90b8e-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="90b8e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90b8e-108">Description</span></span>

<span data-ttu-id="90b8e-109">Komut `dotnet add reference` , projeye proje başvuruları eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="90b8e-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="90b8e-110">Komutu çalıştırdıktan sonra `<ProjectReference>` öğeler proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="90b8e-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="90b8e-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="90b8e-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="90b8e-112">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90b8e-112">Specifies the project file.</span></span> <span data-ttu-id="90b8e-113">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="90b8e-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="90b8e-114">Eklenecek projeden projeye (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="90b8e-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="90b8e-115">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="90b8e-115">Specify one or more projects.</span></span> <span data-ttu-id="90b8e-116">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="90b8e-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="90b8e-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="90b8e-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="90b8e-118">Yalnızca tfd biçimini kullanarak belirli bir [çerçeveyi](../../standard/frameworks.md) hedeflerken proje başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="90b8e-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

- **`-h|--help`**

  <span data-ttu-id="90b8e-119">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="90b8e-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="90b8e-120">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesini sağlar (genellikle kimlik doğrulamasını tamamlayacak şekilde kullanılır).</span><span class="sxs-lookup"><span data-stu-id="90b8e-120">Allows the command to stop and wait for user input or action (typically used to complete authentication).</span></span> <span data-ttu-id="90b8e-121">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="90b8e-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="90b8e-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90b8e-122">Examples</span></span>

- <span data-ttu-id="90b8e-123">Proje başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="90b8e-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="90b8e-124">Geçerli dizindeki projeye birden çok proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="90b8e-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="90b8e-125">Linux/Unix üzerinde glob bir model kullanarak birden çok proje başvurusu ekleme:</span><span class="sxs-lookup"><span data-stu-id="90b8e-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```

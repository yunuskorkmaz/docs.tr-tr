---
title: DotNet-başvuru komutu Ekle
description: DotNet başvuru komutu, proje başvurularına proje eklemek için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 79c8a787079e02f6cf227820c24bb4157b0292c6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522772"
---
# <a name="dotnet-add-reference"></a>DotNet-başvuru Ekle

**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference`-projeden projeye (P2P) başvuruları ekler.

## <a name="synopsis"></a>Özeti

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Açıklama

@No__t_0 komutu bir projeye proje başvuruları eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra, `<ProjectReference>` öğeleri proje dosyasına eklenir.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

- **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

- **`PROJECT_REFERENCES`**

  Eklenecek projeden projeye (P2P) başvuruları. Bir veya daha fazla proje belirtin. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken proje başvuruları ekler.

- **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

## <a name="examples"></a>Örnekler

- Proje başvurusu Ekle:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Geçerli dizindeki projeye birden çok proje başvurusu ekleyin:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Linux/Unix üzerinde glob bir model kullanarak birden çok proje başvurusu ekleme:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```

---
title: dotnet referans komutu ekleyin
description: Dotnet add reference komutu proje başvurularına proje eklemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503794"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Adı

`dotnet add reference`- Projeden projeye (P2P) başvurular ekler.

## <a name="synopsis"></a>Özet

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Açıklama

Komut, `dotnet add reference` projeye proje başvuruları eklemek için kullanışlı bir seçenek sağlar. Komutu çalıştırdıktan `<ProjectReference>` sonra, öğeler proje dosyasına eklenir.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizini arar.

- **`PROJECT_REFERENCES`**

  Projeden projeye (P2P) başvurular eklemek. Bir veya daha fazla proje belirtin. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) Unix/Linux tabanlı sistemlerde desteklenir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken proje referansları ekler.

- **`--interactive`**

  Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir. .NET Core 3.0 SDK'dan beri mevcuttur.

## <a name="examples"></a>Örnekler

- Proje başvurusu ekleyin:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Geçerli dizinde projeye birden çok proje referansı ekleyin:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Linux/Unix üzerinde globbing deseni kullanarak birden çok proje başvurusu ekleyin:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```

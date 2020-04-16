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
# <a name="dotnet-add-reference"></a>dotnet add reference

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet add reference`- Projeden projeye (P2P) başvurular ekler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

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

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken proje referansları ekler.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

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

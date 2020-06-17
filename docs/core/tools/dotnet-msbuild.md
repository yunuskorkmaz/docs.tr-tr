---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803168"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet msbuild`-Bir projeyi ve tüm bağımlılıklarını oluşturur. Note: birden çok varsa bir çözüm veya proje dosyasının belirtilmesi gerekebilir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>Açıklama

`dotnet msbuild`Komut, tam Işlevli MSBuild 'e erişim sağlar.

Komutu, yalnızca SDK stilindeki projeler için mevcut MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir. Seçenekler aynı. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

[DotNet derleme](dotnet-build.md) komutu ile eşdeğerdir `dotnet msbuild -restore` . Projeyi derlemek istemediğinizde ve çalıştırmak istediğiniz belirli bir hedef varsa, veya öğesini kullanın `dotnet build` `dotnet msbuild` ve hedefi belirtin.

## <a name="examples"></a>Örnekler

- Bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild
  ```

- Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Yayımla hedefini çalıştırın ve RID için yayımlayın `osx.10.11-x64` :

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```

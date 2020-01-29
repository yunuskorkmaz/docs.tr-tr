---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733199"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet msbuild`-bir projeyi ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

`dotnet msbuild` komutu, tam işlevli MSBuild 'e erişim sağlar.

Komutu, yalnızca SDK stilindeki projeler için mevcut MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir. Seçenekler aynı. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

[DotNet derleme](dotnet-build.md) komutu `dotnet msbuild -restore -target:Build`eşdeğerdir. [DotNet derlemesi](dotnet-build.md) , proje oluşturmak için daha yaygın olarak kullanılır, ancak her zaman derleme hedefini çalıştırdığı için, projeyi derlemek istemediğinizde `dotnet msbuild` kullanabilirsiniz. Örneğin, projeyi oluşturmadan çalıştırmak istediğiniz belirli bir hedef varsa `dotnet msbuild` kullanın ve hedefi belirtin.

## <a name="examples"></a>Örnekler

* Bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild
  ```

* Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* Yayımla hedefini çalıştırın ve RID `osx.10.11-x64` için yayımlayın:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```

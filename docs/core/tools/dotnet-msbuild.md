---
title: DotNet MSBuild komutu
description: DotNet MSBuild komutu, MSBuild komut satırına erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117697"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet msbuild`-Bir projeyi ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

Komut `dotnet msbuild` , tam işlevli MSBuild 'e erişim sağlar.

Komutu, yalnızca SDK stili proje için mevcut olan MSBuild komut satırı istemcisiyle aynı yeteneklere sahiptir. Seçenekler aynı. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

[DotNet derleme](dotnet-build.md) komutu ile `dotnet msbuild -restore -target:Build`eşdeğerdir. `dotnet build`, proje oluşturmak için daha yaygın olarak kullanılır, `dotnet msbuild` ancak size daha fazla denetim sağlar. Örneğin, çalıştırmak istediğiniz belirli bir hedef varsa (derleme hedefini çalıştırmadan) muhtemelen kullanmak `dotnet msbuild`istersiniz.

## <a name="examples"></a>Örnekler

* Bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild
  ```

* Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* Yayımla hedefini çalıştırın ve `osx.10.11-x64` RID için yayımlayın:

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* SDK tarafından eklenen tüm hedefleri içeren tüm projeyi görüntüleyin:

  ```dotnetcli
  dotnet msbuild -pp
  ```

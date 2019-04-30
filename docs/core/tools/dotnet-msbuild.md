---
title: DotNet msbuild komut
description: Dotnet msbuild komut MSBuild komut satırını erişim sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: f025b5b92e57c7b804b9bdd59c8b4a4a806796da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648704"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet msbuild` -Bir proje ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Synopsis

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

`dotnet msbuild` Komutu tam olarak işlevsel bir MSBuild erişim sağlar.

Komutu yalnızca SDK stilinde proje var olan MSBuild komut satırı istemcisi tam aynı özellikleri vardır. Seçenekler tüm aynıdır. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

[Dotnet derleme](dotnet-build.md) komutu için eşdeğer `dotnet msbuild -restore -target:Build`. `dotnet build` projeleri oluşturmak için daha yaygın olarak kullanılır, ancak `dotnet msbuild` daha fazla denetim sağlar. (Çalışan yapı hedefi olmadan) çalıştırmak istediğiniz belirli bir hedef varsa, örneğin, büyük olasılıkla kullanmak istediğiniz `dotnet msbuild`.

## <a name="examples"></a>Örnekler

* Bir proje ve bağımlılıkları derleme:

  ```console
  dotnet msbuild
  ```

* Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* Yayımlama hedefi çalıştırın ve yayımlama için `osx.10.11-x64` RID:

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* SDK tarafından eklenen tüm hedefleri ile tüm proje bakın:

  ```console
  dotnet msbuild -pp
  ```
---
title: dotnet msbuild komutu
description: dotnet msbuild komutu MSBuild komut satırına erişim sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503668"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet msbuild`- Bir proje ve tüm bağımlılıkları oluşturur.

## <a name="synopsis"></a>Özet

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

Komut, `dotnet msbuild` tamamen işlevsel bir MSBuild erişimi sağlar.

Komut, yalnızca SDK tarzı projeler için varolan MSBuild komut satırı istemcisi ile aynı özelliklere sahiptir. Seçeneklerin hepsi aynı. Kullanılabilir seçenekler hakkında daha fazla bilgi için [MSBuild komut satırı başvurusuna](/visualstudio/msbuild/msbuild-command-line-reference)bakın.

[Dotnet yapı](dotnet-build.md) komutu `dotnet msbuild -restore -target:Build`' ya eşdeğerdir. [dotnet yapı](dotnet-build.md) daha yaygın olarak proje oluşturmak için kullanılır, ancak her `dotnet msbuild` zaman yapı hedefini çalıştırdığından, projeyi oluşturmak istemediğinde kullanabilirsiniz. Örneğin, projeyi oluşturmadan çalıştırmak istediğiniz belirli bir hedefiniz `dotnet msbuild` varsa, hedefi kullanın ve belirtin.

## <a name="examples"></a>Örnekler

- Bir proje ve bağımlılıkları oluşturun:

  ```dotnetcli
  dotnet msbuild
  ```

- Sürüm yapılandırmasını kullanarak bir proje ve bağımlılıkları oluşturun:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Yayımlama hedefini çalıştırın `osx.10.11-x64` ve RID için yayımlayın:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- SDK tarafından dahil edilen tüm hedeflerle tüm projeyi görün:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```

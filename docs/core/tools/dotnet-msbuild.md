---
title: DotNet msbuild command - .NET Core CLI
description: Dotnet msbuild komut MSBuild komut satırını erişim sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082337"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet msbuild` -Bir proje ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

`dotnet msbuild` Komutu tam olarak işlevsel bir MSBuild erişim sağlar.

Komutu, var olan MSBuild komut satırı istemcisi tam aynı özellikleri vardır. Seçenekler tüm aynıdır. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Örnekler

Bir proje ve bağımlılıkları derleme:

`dotnet msbuild`

Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:

`dotnet msbuild -p:Configuration=Release`

Yayımlama hedefi çalıştırın ve yayımlama için `osx.10.11-x64` RID:

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

SDK tarafından eklenen tüm hedefleri ile tüm proje bakın:

`dotnet msbuild -pp`

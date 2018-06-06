---
title: DotNet msbuild komut - .NET Core CLI
description: Dotnet msbuild komut MSBuild komut satırında erişim sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696851"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet msbuild` -Bir proje ve tüm bağımlılıkları oluşturur.

## <a name="synopsis"></a>Özet

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

`dotnet msbuild` Komutu tam olarak işlevsel MSBuild erişim sağlar.

Komut varolan MSBuild komut satırı istemcisi tam aynı özelliklerine sahiptir. Tümü aynı seçeneklerdir. Kullanılabilir seçenekler hakkında daha fazla bilgi için bkz: [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Örnekler

Proje ve bağımlılıklarını oluşturun:

`dotnet msbuild`

Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:

`dotnet msbuild /p:Configuration=Release`

Yayımlama hedefi çalıştırın ve için Yayımlama `osx.10.11-x64` RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

SDK tarafından eklenen tüm hedefleri olan tüm proje bakın:

`dotnet msbuild /pp`

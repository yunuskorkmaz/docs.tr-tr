---
title: DotNet msbuild komut - .NET Core CLI
description: "Dotnet msbuild komut MSBuild komut satırında erişim sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 682b49d44c0fb8242eeb3cb8bf4d158f73b4b9a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet msbuild`-Bir proje ve tüm bağımlılıkları oluşturur.

## <a name="synopsis"></a>Özet

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Açıklama

`dotnet msbuild` Komutu tam olarak işlevsel MSBuild erişim sağlar.

Komut varolan MSBuild komut satırı istemcisi tam aynı özelliklerine sahiptir. Tümü aynı seçeneklerdir. Kullanım [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) kullanılabilir seçenekler hakkında bilgi edinmek için. 

## <a name="examples"></a>Örnekler

Proje ve bağımlılıklarını oluşturun:

`dotnet msbuild`

Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:

`dotnet msbuild /p:Configuration=Release`

Yayımlama hedefi çalıştırın ve için Yayımlama `osx.10.11-x64` RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

SDK tarafından eklenen tüm hedefleri olan tüm proje bakın:

`dotnet msbuild /pp`

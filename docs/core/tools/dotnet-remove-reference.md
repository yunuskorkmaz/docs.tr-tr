---
title: DotNet Kaldır başvuru command - .NET Core CLI
description: Dotnet Kaldır başvuru komutu proje için proje başvuruları kaldırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696237"
---
# <a name="dotnet-remove-reference"></a>DotNet Kaldır başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet remove reference` -Proje Proje başvuruları kaldırır.

## <a name="synopsis"></a>Özet

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet remove reference` Komutu proje başvuruları bir projeden kaldırmak için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Hedef proje dosyası. Belirtilmezse, komut için geçerli dizin arar.

`PROJECT_REFERENCES`

Kaldırmak için proje proje (P2P) başvuruyor. Bir veya birden çok proje belirtebilirsiniz. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-f|--framework <FRAMEWORK>`

Yalnızca belirli bir hedeflerken başvuru kaldırır [framework](../../standard/frameworks.md).

## <a name="examples"></a>Örnekler

Proje başvurusu belirtilen projeden kaldırın:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Geçerli dizin projede birden çok proje başvuruları kaldırın:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

UNIX/Linux üzerinde glob desenini kullanarak birden çok proje başvuruları kaldırın:

`dotnet remove app/app.csproj reference **/*.csproj`

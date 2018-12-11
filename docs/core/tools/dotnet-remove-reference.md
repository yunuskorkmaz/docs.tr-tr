---
title: DotNet Kaldır başvuru komutu
description: Dotnet remove başvuru komutu, projeden projeye başvuruları kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170619"
---
# <a name="dotnet-remove-reference"></a>DotNet başvuru Kaldır

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet remove reference` -Projeden projeye başvurular kaldırır.

## <a name="synopsis"></a>Özeti

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet remove reference` Komutu bir projeden projeye başvuruları kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Hedef proje dosyası. Belirtilmezse, komut için geçerli dizinde arar.

`PROJECT_REFERENCES`

Projeden projeye (P2P) kaldırmak için başvurur. Bir veya birden çok proje belirtebilirsiniz. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-f|--framework <FRAMEWORK>`

Yalnızca belirli bir hedeflenirken başvuruyu kaldırır [framework](../../standard/frameworks.md).

## <a name="examples"></a>Örnekler

Bir proje başvurusu belirtilen projeden kaldır:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Geçerli dizindeki bir projeden birden çok proje başvuruları kaldırın:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

UNIX/Linux üzerinde bir glob deseni kullanılarak birden çok proje başvuruları kaldırın:

`dotnet remove app/app.csproj reference **/*.csproj`

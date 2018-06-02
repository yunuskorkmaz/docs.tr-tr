---
title: DotNet listesi başvuru command - .NET Core CLI
description: Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 821e6d276af44bf984c8ac1b42b4e954dbe69556
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697189"
---
# <a name="dotnet-list-reference"></a>DotNet listesi başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet list reference` -Proje Proje başvurular listelenmektedir.

## <a name="synopsis"></a>Özet

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` Komutu belirli bir projenin için liste proje başvuruları için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Başvuruları listelemek için kullanılacak proje dosyasını belirtir. Belirtilmezse, komut bir proje dosyası için geçerli dizini arar.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Belirtilen proje için proje başvuruları listesi:

`dotnet list app/app.csproj reference`

Geçerli dizindeki proje için proje başvuruları listesi:

`dotnet list reference`
---
title: DotNet listesi başvuru command - .NET Core CLI
description: Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 24cb1124fc3f8707afe727e6a73d35d5dde39937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-list-reference"></a>DotNet listesi başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet list reference` -Projeyi project başvurular listelenmektedir.

## <a name="synopsis"></a>Özet

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` Komutu belirli bir projenin için liste proje başvuruları için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Başvuruları listelemek için kullanılacak proje dosyasını belirtir. Belirtilmezse, komut bir proje dosyası için geçerli dizini arayın.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Belirtilen proje için proje başvuruları listesi:

`dotnet list app/app.csproj reference`

Geçerli dizindeki proje için proje başvuruları listesi:

`dotnet list reference`

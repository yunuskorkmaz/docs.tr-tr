---
title: "DotNet listesi başvuru command - .NET Core CLI"
description: "Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-list-reference"></a>DotNet listesi başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet list reference`-Projeyi project başvurular listelenmektedir.

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

---
title: DotNet listesi başvuru command - .NET Core CLI
description: Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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

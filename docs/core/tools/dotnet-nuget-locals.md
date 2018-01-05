---
title: DotNet nuget Yereller komutu - .NET Core CLI
description: "Dotnet nuget Yereller komutu temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9c8df8e457a9883b86abd0505c0c682d849bc7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-locals"></a>DotNet nuget yerel öğeler

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget locals`-Temizler veya yerel NuGet kaynakları listeler.

## <a name="synopsis"></a>Özet

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet nuget locals` Komutu temizler veya http isteği önbelleği, geçici önbelleği ya da makine genelinde genel paketler klasörü yerel NuGet kaynakları listeler.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Aşağıdaki değerlerden biri:

* `all`-Belirtilen işlem için tüm önbellek türleri uygulandığını gösterir: http isteği önbellek, genel paketleri önbellek ve geçici önbelleği.
* `http-cache`-Belirtilen işlem yalnızca http isteği önbelleği uygulandığını gösterir. Bir önbellek konumları etkilenmez.
* `global-packages`-Belirtilen işlem yalnızca genel paketleri önbelleği uygulandığını gösterir. Bir önbellek konumları etkilenmez.
* `temp`-Belirtilen işlem yalnızca geçici önbelleğine uygulandığını gösterir. Bir önbellek konumları etkilenmez.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-c|--clear`

Temizle seçeneği belirtilen önbellek türü üzerinde NET bir işlemi gerçekleştirir. Önbellek dizin içeriğini silinen yinelemeli olarak var. Yürütülen kullanıcı/grup, önbellek dizinlerdeki dosyalara izni olmalıdır. Aksi durumda, dosyaların/klasörlerin hangi değil silinmesinden belirten bir hata görüntülenir.

`-l|--list`

Liste seçeneği, belirtilen önbellek türü konumu göstermek için kullanılır. 

`--force-english-output`

Zorlar komut satırı, İngilizce çıktı.

## <a name="examples"></a>Örnekler

Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:

`dotnet nuget locals –l all`

Yerel http önbellek dizin yolunu görüntüler:

`dotnet nuget locals --list http-cache`

Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:

`dotnet nuget locals --clear all`

Yerel paketler genel önbellek dizindeki tüm dosyaları siler:

`dotnet nuget locals -c global-packages`

Yerel geçici önbelleği dizindeki tüm dosyaları siler:

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Sorun giderme

Kullanırken yaygın sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleği yönetme](/nuget/consume-packages/managing-the-nuget-cache).
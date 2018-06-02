---
title: DotNet nuget Yereller komutu - .NET Core CLI
description: Dotnet nuget Yereller komutu temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696877"
---
# <a name="dotnet-nuget-locals"></a>DotNet nuget yerel öğeler

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet nuget locals` -Temizler veya yerel NuGet kaynakları listeler.

## <a name="synopsis"></a>Özet

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget locals` Komutu temizler veya http isteği önbelleği, geçici önbelleği ya da makine genelinde genel paketler klasörü yerel NuGet kaynakları listeler.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Liste veya temizlemek için önbellek konumu. Aşağıdaki değerlerden birini kabul eder:

* `all` -Belirtilen işlem için tüm önbellek türleri uygulandığını gösterir: http isteği önbellek, genel paketleri önbellek ve geçici önbelleği.
* `http-cache` -Belirtilen işlem yalnızca http isteği önbelleği uygulandığını gösterir. Bir önbellek konumları etkilenmez.
* `global-packages` -Belirtilen işlem yalnızca genel paketleri önbelleği uygulandığını gösterir. Bir önbellek konumları etkilenmez.
* `temp` -Belirtilen işlem yalnızca geçici önbelleğine uygulandığını gösterir. Bir önbellek konumları etkilenmez.

## <a name="options"></a>Seçenekler

`--force-english-output`

Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-c|--clear`

Temizle seçeneği belirtilen önbellek türündeki clear işlemini yürütür. Önbellek dizin içeriğini silinen yinelemeli olarak var. Yürütülen kullanıcı/grup, önbellek dizinlerdeki dosyalara izni olmalıdır. Aksi durumda, temizlenmiş doğru dosyaların/klasörlerin belirten bir hata görüntülenir.

`-l|--list`

Liste seçeneği, belirtilen önbellek türü konumu göstermek için kullanılır.

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
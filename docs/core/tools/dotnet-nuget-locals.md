---
title: DotNet NuGet Yereller komutu
description: DotNet NuGet Yereller komutu http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 482e841d3b402084eb8c7f2456779f1600a5dd19
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117621"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget locals`-Yerel NuGet kaynaklarını temizler veya listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget locals` Komut, http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasöründeki yerel NuGet kaynaklarını temizler veya listeler.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Listelemek veya temizlemek için önbellek konumu. Aşağıdaki değerlerden birini kabul eder:

  * `all`-Belirtilen işlemin tüm önbellek türlerine uygulandığını belirtir: http-istek önbelleği, genel paketler önbelleği ve geçici önbellek.
  * `http-cache`-Belirtilen işlemin yalnızca http istek önbelleğine uygulanacağını gösterir. Diğer önbellek konumları etkilenmez.
  * `global-packages`-Belirtilen işlemin yalnızca genel paketler önbelleğine uygulanacağını gösterir. Diğer önbellek konumları etkilenmez.
  * `temp`-Belirtilen işlemin yalnızca geçici önbelleğe uygulandığını belirtir. Diğer önbellek konumları etkilenmez.

## <a name="options"></a>Seçenekler

* **`--force-english-output`**

  Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`-c|--clear`**

  Clear seçeneği, belirtilen önbellek türü üzerinde açık bir işlem yürütür. Önbellek dizinlerinin içeriği yinelemeli olarak silinir. Yürütülen Kullanıcı/Grup, önbellek dizinlerindeki dosyalar üzerinde izne sahip olmalıdır. Aksi takdirde, temizlenmeyen dosyaları/klasörleri gösteren bir hata görüntülenir.

* **`-l|--list`**

  Liste seçeneği, belirtilen önbellek türünün konumunu göstermek için kullanılır.

## <a name="examples"></a>Örnekler

* Tüm yerel önbellek dizinlerinin (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:

  ```dotnetcli
  dotnet nuget locals –l all
  ```

* Yerel http önbelleği dizininin yolunu görüntüler:

  ```dotnetcli
  dotnet nuget locals --list http-cache
  ```

* Tüm yerel önbellek dizinlerindeki tüm dosyaları temizler (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini):

  ```dotnetcli
  dotnet nuget locals --clear all
  ```

* Yerel genel paketler önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals -c global-packages
  ```

* Yerel geçici önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Sorun giderme

`dotnet nuget locals` Komutunu kullanırken yaygın sorunlar ve hatalar hakkında bilgi için bkz. [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).

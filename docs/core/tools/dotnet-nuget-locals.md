---
title: DotNet NuGet Yereller komutu
description: DotNet NuGet Yereller komutu http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0cf025f91a7582fafc401799cd1d8b933b087535
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202471"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget locals`-Yerel NuGet kaynaklarını temizler veya listeler.

## <a name="synopsis"></a>Özeti

```console
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

  ```console
  dotnet nuget locals –l all
  ```

* Yerel http önbelleği dizininin yolunu görüntüler:

  ```console
  dotnet nuget locals --list http-cache
  ```

* Tüm yerel önbellek dizinlerindeki tüm dosyaları temizler (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini):

  ```console
  dotnet nuget locals --clear all
  ```

* Yerel genel paketler önbellek dizinindeki tüm dosyaları temizler:

  ```console
  dotnet nuget locals -c global-packages
  ```

* Yerel geçici önbellek dizinindeki tüm dosyaları temizler:

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Sorun giderme

`dotnet nuget locals` Komutunu kullanırken yaygın sorunlar ve hatalar hakkında bilgi için bkz. [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).

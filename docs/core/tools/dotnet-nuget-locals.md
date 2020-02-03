---
title: DotNet NuGet Yereller komutu
description: DotNet NuGet Yereller komutu http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: b57c127650555e412af08df6656fb62d75c8ed7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734086"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget locals`-yerel NuGet kaynaklarını temizler veya listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget locals` komutu, http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasöründeki yerel NuGet kaynaklarını temizler veya listeler.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Listelemek veya temizlemek için önbellek konumu. Aşağıdaki değerlerden birini kabul eder:

  * `all`-belirtilen işlemin tüm önbellek türlerine uygulandığını gösterir: http-istek önbelleği, genel paketler önbelleği ve geçici önbellek.
  * `http-cache`-belirtilen işlemin yalnızca http istek önbelleğine uygulanacağını gösterir. Diğer önbellek konumları etkilenmez.
  * `global-packages`-belirtilen işlemin yalnızca genel paketler önbelleğine uygulanacağını gösterir. Diğer önbellek konumları etkilenmez.
  * `temp`-belirtilen işlemin yalnızca geçici önbelleğe uygulandığını belirtir. Diğer önbellek konumları etkilenmez.

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
  dotnet nuget locals all –l
  ```

* Yerel http önbelleği dizininin yolunu görüntüler:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* Tüm yerel önbellek dizinlerindeki tüm dosyaları temizler (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* Yerel genel paketler önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* Yerel geçici önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Sorun giderme

`dotnet nuget locals` komutunu kullanırken yaygın sorunlar ve hatalar hakkında bilgi için bkz. [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).

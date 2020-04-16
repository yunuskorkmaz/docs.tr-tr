---
title: dotnet nuget locals komutu
description: Dotnet nuget locals komutu, http isteği önbelleği, geçici önbellek veya makine çapında ki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 5b421b5058528a93c7be58eef2932937cc9cc12d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463527"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget locals`- Yerel NuGet kaynaklarını temizler veya listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]

dotnet nuget locals -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget locals` yerel NuGet kaynaklarını http isteği önbelleği, geçici önbellek veya makine çapında ki genel paketler klasöründe temizler veya listeler.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`CACHE_LOCATION`**

  Listelemek veya temizlemek için önbellek konumu. Aşağıdaki değerlerden birini kabul eder:

  * `all`- Belirtilen işlemin tüm önbellek türlerine uygulandığını gösterir: http-request önbelleği, genel paketler önbelleği ve geçici önbellek.
  * `http-cache`- Belirtilen işlemin yalnızca http isteği önbelleğine uygulandığını gösterir. Diğer önbellek konumları etkilenmez.
  * `global-packages`- Belirtilen işlemin yalnızca genel paketler önbelleğine uygulandığını gösterir. Diğer önbellek konumları etkilenmez.
  * `temp`- Belirtilen işlemin yalnızca geçici önbelleğe uygulandığını gösterir. Diğer önbellek konumları etkilenmez.

## <a name="options"></a>Seçenekler

- **`--force-english-output`**

  Uygulamayı değişmez, İngilizce tabanlı bir kültür kullanarak çalıştırmaya zorlar.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-c|--clear`**

  Açık seçenek, belirtilen önbellek türünde net bir işlem yürütür. Önbellek dizinlerinin içeriği özyinelemeli olarak silinir. Çalıştıran kullanıcı/grup önbellek dizinlerinde dosyalar için izin olmalıdır. Değilse, temizlenmeyen dosyaları/klasörleri gösteren bir hata görüntülenir.

- **`-l|--list`**

  Liste seçeneği, belirtilen önbellek türünün konumunu görüntülemek için kullanılır.

## <a name="examples"></a>Örnekler

- Tüm yerel önbellek dizinlerinin (http önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Yerel http-önbellek dizininin yolunu görüntüler:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Tüm yerel önbellek dizinlerinden (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini) tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Yerel genel paketler önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Yerel geçici önbellek dizinindeki tüm dosyaları temizler:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Sorun giderme

`dotnet nuget locals` Komutu kullanırken sık karşılaşılan sorunlar ve hatalar hakkında bilgi için [NuGet önbelleğini yönetme'ye](/nuget/consume-packages/managing-the-nuget-cache)bakın.

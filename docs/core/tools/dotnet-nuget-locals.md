---
title: DotNet nuget Yereller komutu
description: Dotnet nuget Yereller komutu kaldırır veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketler klasörü gibi yerel NuGet kaynakları listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 6436bbaee7ae50f4b225c32b2245c737b0d359c3
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539263"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet nuget locals` -Temizler veya yerel NuGet kaynakları listeler.

## <a name="synopsis"></a>Synopsis

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet nuget locals` Komut temizler veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketleri klasörünü yerel NuGet kaynakları listeler.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Liste veya temizlemek için önbellek konumu. Aşağıdaki değerlerden birini kabul eder:

  * `all` -Tüm önbellek türleri için belirtilen işlem geçerli olduğunu gösterir: http istek önbelleği, genel paketleri yazma önbelleği ve geçici önbellek.
  * `http-cache` -Belirtilen işlem yalnızca http isteğini önbelleğe uygulandığını gösterir. Bir önbellek konumlarını etkilenmez.
  * `global-packages` -Belirtilen işlem yalnızca genel paketleri önbelleğe uygulandığını gösterir. Bir önbellek konumlarını etkilenmez.
  * `temp` -Belirtilen işlem yalnızca geçici önbelleğe uygulandığını gösterir. Bir önbellek konumlarını etkilenmez.

## <a name="options"></a>Seçenekler

* **`--force-english-output`**

  Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`-c|--clear`**

  Açık seçeneği, belirtilen önbellek türü açık bir işlem yürütür. Önbellek dizin içeriğini silinen yinelemeli olarak var. Yürütülen kullanıcı/Grup dosyalar için önbellek dizinleri de iznine sahip olmalıdır. Aksi durumda, seçili olmayan dosyaların/klasörlerin belirten bir hata görüntülenir.

* **`-l|--list`**

  Liste seçeneği, belirtilen önbellek türü konumunu görüntülemek için kullanılır.

## <a name="examples"></a>Örnekler

* Tüm yerel önbellek dizini (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:

  ```console
  dotnet nuget locals –l all
  ```

* Yerel http önbellek dizin yolunu görüntüler:

  ```console
  dotnet nuget locals --list http-cache
  ```

* Tüm yerel önbellek dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:

  ```console
  dotnet nuget locals --clear all
  ```

* Yerel paketler genel önbellek dizindeki tüm dosyaları siler:

  ```console
  dotnet nuget locals -c global-packages
  ```

* Yerel geçici önbellek dizindeki tüm dosyaları siler:

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Sorun giderme

Kullanırken sık karşılaşılan sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).

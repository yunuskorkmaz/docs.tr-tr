---
title: dotnet nuget push komutu
description: Dotnet nuget push komutu bir paketi sunucuya iter ve yayımlar.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503666"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget push`- Bir paketi sunucuya iter ve yayınlar.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Açıklama

Komut `dotnet nuget push` bir paketi sunucuya iter ve yayımlar. Push komutu, sistemin NuGet config dosyasında veya config dosyaları zincirinde bulunan sunucu ve kimlik bilgilerini kullanır. Config dosyaları hakkında daha fazla bilgi için [NuGet Davranışını Yapılandırma'ya](/nuget/consume-packages/configuring-nuget-behavior)bakın. NuGet'in varsayılan yapılandırması *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS) yüklenerek elde edilir, ardından sürücü kökünden başlayıp geçerli dizinde biten herhangi bir *nuget.config* veya *.nuget\nuget.config* yüklenir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`ROOT`**

  Itilecek pakete dosya yolunu belirtir.

## <a name="options"></a>Seçenekler

- **`-d|--disable-buffering`**

  Bellek kullanımını azaltmak için bir HTTP(S) sunucusuna bastırırken arabelleği devre dışı düşürür.

- **`--force-english-output`**

  Uygulamayı değişmez, İngilizce tabanlı bir kültür kullanarak çalıştırmaya zorlar.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun engellenmesine izin verir ve kimlik doğrulama gibi işlemler için el ile eylem gerektirir. Seçenek .NET Core 2.2 SDK'dan beri mevcuttur.

- **`-k|--api-key <API_KEY>`**

  Sunucu için API anahtarı.

- **`-n|--no-symbols`**

  Sembolleri itmiyor (mevcut olsa bile).

- **`--no-service-endpoint`**

  Kaynak URL'ye "api/v2/package" eklenmemiştir. Seçenek .NET Core 2.1 SDK'dan beri mevcuttur.

- **`-s|--source <SOURCE>`**

  Sunucu URL'sini belirtir. Config değeri `DefaultPushSource` NuGet config dosyasında ayarlılmadığı sürece bu seçenek gereklidir.

- **`--skip-duplicate`**

  Bir HTTP(S) sunucusuna birden çok paket iterken, herhangi bir 409 Çakışma yanıtını bir uyarı olarak ele alır, böylece itme devam edebilir. .NET Core 3.1 SDK'dan beri mevcuttur.

- **`-sk|--symbol-api-key <API_KEY>`**

  Sembol sunucusu için API anahtarı.

- **`-ss|--symbol-source <SOURCE>`**

  Sembol sunucu URL'sini belirtir.

- **`-t|--timeout <TIMEOUT>`**

  Bir sunucuya saniyeler içinde itmek için zaman anına göre belirtir. Varsayılan olarak 300 saniye (5 dakika) olarak tanımlanır. 0 (sıfır saniye) belirtmek varsayılan değeri uygular.

## <a name="examples"></a>Örnekler

- *Foo.nupkg'ı* varsayılan itme kaynağına iter ve bir API anahtarı belirtir:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- *Foo.nupkg'ı* resmi NuGet sunucusuna itin ve bir API anahtarı belirtin:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * *Foo.nupkg'ı* özel push `https://customsource`kaynağına itin, API tuşu belirterek:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- *Foo.nupkg'ı* varsayılan itme kaynağına iter:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- *Foo.symbols.nupkg'ı* varsayılan semboller kaynağına iter:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- *Foo.nupkg'ı* varsayılan itme kaynağına iter ve 360 saniyelik bir zaman ayarı belirtir:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Geçerli dizindeki tüm *.nupkg* dosyalarını varsayılan itme kaynağına iter:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Bu komut işe yaramazsa, SDK'nın (.NET Core 2.1 SDK ve önceki sürümlerinde) eski sürümlerinde bulunan bir hatadan kaynaklanıyor olabilir.
  > Bunu düzeltmek için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın:`dotnet nuget push **/*.nupkg`

- 409 Çakışma yanıtı bir HTTP(S) sunucusu tarafından döndürülse bile tüm *.nupkg* dosyalarını iter:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

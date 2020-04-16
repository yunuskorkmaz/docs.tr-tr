---
title: dotnet nuget silme komutu
description: Dotnet-nuget-delete komutu bir paketi sunucudan siler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4fa4f24adba251d7872986de4a8b1a63203c36c3
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463579"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Bu makale şu şekilde dir:** ✔️ .NET Core 1.x SDK ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Adı

`dotnet nuget delete`- Bir paketi sunucudan siler veya listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [--no-service-endpoint]
    [--non-interactive] [-s|--source <SOURCE>]

dotnet nuget delete -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget delete` bir paketi sunucudan siler veya boşaltıyor. [nuget.org](https://www.nuget.org/)için, eylem paketi unlist etmektir.

## <a name="arguments"></a>Bağımsız Değişkenler

* **`PACKAGE_NAME`**

  Silmek için paketin adı/kimliği.

* **`PACKAGE_VERSION`**

  Paketin sürümü silinecek.

## <a name="options"></a>Seçenekler

* **`--force-english-output`**

  Uygulamayı değişmez, İngilizce tabanlı bir kültür kullanarak çalıştırmaya zorlar.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun engellenmesine izin verir ve kimlik doğrulama gibi işlemler için el ile eylem gerektirir. Seçenek .NET Core 2.2 SDK'dan beri mevcuttur.

* **`-k|--api-key <API_KEY>`**

  Sunucu için API anahtarı.

* **`--no-service-endpoint`**

  Kaynak URL'ye "api/v2/package" eklenmemiştir. Seçenek .NET Core 2.1 SDK'dan beri mevcuttur.

* **`--non-interactive`**

  Kullanıcı girişi veya onayları istenmez.

* **`-s|--source <SOURCE>`**

  Sunucu URL'sini belirtir. nuget.org için desteklenen URL'ler `https://www.nuget.org/api/v3`, `https://www.nuget.org/api/v2/package` `https://www.nuget.org`ve . Özel akışlar için ana bilgisayar adını `%hostname%/api/v3`değiştirin (örneğin, ).

## <a name="examples"></a>Örnekler

* Paketin `Microsoft.AspNetCore.Mvc`sürüm 1.0'ını siler:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Paketin `Microsoft.AspNetCore.Mvc`sürüm 1.0'ını siler, kullanıcıdan kimlik bilgileri veya diğer girişler için istenmez:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```

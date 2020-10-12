---
title: DotNet NuGet Verify komutu
description: DotNet NuGet Verify komutu imzalı bir paketi doğrular.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957169"
---
# <a name="dotnet-nuget-verify"></a>DotNet NuGet doğrulaması

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100-RC. 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget verify` -İmzalı bir NuGet paketini doğrular.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a>Açıklama

`dotnet nuget verify`Komut imzalı bir NuGet paketini doğrular.

## <a name="arguments"></a>Bağımsız değişkenler

- **`package-path(s)`**

  Doğrulanacak paket (ler) in dosya yolunu belirtir. Birden çok paketi doğrulamak için birden çok konum bağımsız değişkeni geçirilebilir.

## <a name="options"></a>Seçenekler

- **`--all`**

  Tüm doğrulamaları, paketler üzerinde gerçekleştirilmesi gerektiğini belirtir. Varsayılan olarak, yalnızca `signatures` doğrulanır.

> [!NOTE]
> Bu komut şu anda yalnızca `signature` doğrulamayı desteklemektedir.

- **`--certificate-fingerprint <FINGERPRINT>`**

  İmzalayan sertifikasının belirtilen `SHA256` parmak izlerinden biriyle eşleştiğini doğrulayın. Birden çok parmak izi sağlamak için bu seçeneğin birden çok kez sağlanması sağlanabilir.

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer: `normal`.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- *Foo. nupkg*'yi doğrula:

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- Belirtilen dizindeki birden çok NuGet paketini ( *foo. nupkg* ) ve *tüm. nupkg dosyalarını*doğrulayın:

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- Belirtilen sertifika parmak iziyle *foo. nupkg* imzasını eşleştirenleri doğrula:

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- *Foo. nupkg* imzasını belirtilen sertifika parmak izlerinden biriyle eşleştirirken doğrulayın:

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```

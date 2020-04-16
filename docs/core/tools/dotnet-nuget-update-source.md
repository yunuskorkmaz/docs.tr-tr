---
title: dotnet nuget güncelleme kaynak komutu
description: Dotnet nuget güncelleştirme kaynak komutu, NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463484"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget update source`- Bir NuGet kaynağını güncelleştirin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget update source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

- **`-p|--password <PASSWORD>`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.

- **`-s|--source <SOURCE>`**

  Paket kaynağına giden yol.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.

- **`-u|--username <USER>`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.

- **`--valid-authentication-types <TYPES>`**

  Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi. Sunucu ntlm veya Negotiate'in reklamını yaparsa ve kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, örneğin şirket içi Azure DevOps Server'a sahip bir PAT kullanırken bunu `basic` ayarlayın. Diğer geçerli `negotiate`değerler `kerberos` `ntlm`, `digest`, , ve , içerir, ancak bu değerlerin yararlı olması olası değildir.

## <a name="examples"></a>Örnekler

- Adı olan bir `mySource`kaynağı güncelleştirin:

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

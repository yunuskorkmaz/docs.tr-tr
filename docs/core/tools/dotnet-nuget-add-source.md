---
title: dotnet nuget kaynak komutu eklemek
description: Dotnet nuget add kaynak komutu NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148570"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget kaynak eklemek

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget add source`- NuGet kaynağı ekleyin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget add source` NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_SOURCE_PATH`**

  Paket kaynağına giden yol.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

- **`-n|--name`**

  Kaynağın adı.

- **`-p|--password`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.

- **`-u|--username`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.

- **`--valid-authentication-types`**

  Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi. Sunucu ntlm veya Negotiate'in reklamını yaparsa ve kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, örneğin şirket içi Azure DevOps Server'a sahip bir PAT kullanırken bunu `basic` ayarlayın. Diğer geçerli `negotiate`değerler `kerberos` `ntlm`, `digest`, , ve , içerir, ancak bu değerlerin yararlı olması olası değildir.

## <a name="examples"></a>Örnekler

- Kaynak `nuget.org` olarak ekleyin:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Yerel `c:\packages` kaynak olarak ekleyin:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Kimlik doğrulaması gereken bir kaynak ekleyin:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Kimlik doğrulaması gereken bir kaynak ekleyin (ardından kimlik bilgisi sağlayıcısını yükleyin:

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

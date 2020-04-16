---
title: dotnet nuget kaynak komutu eklemek
description: Dotnet nuget add kaynak komutu NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463595"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget add source`- NuGet kaynağı ekleyin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget add source` NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_SOURCE_PATH`**

  Paket kaynağına giden yol.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

- **`-n|--name <SOURCE_NAME>`**

  Kaynağın adı.

- **`-p|--password <PASSWORD>`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.

- **`-u|--username <USER>`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.

- **`--valid-authentication-types <TYPES>`**

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

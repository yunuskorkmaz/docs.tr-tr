---
title: DotNet NuGet Kaynak Ekle komutu
description: DotNet NuGet Kaynak Ekle komutu, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: df31a2eaba997d0e9fe4f4c2666052fd7c7c2f03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105057"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget add source` -Bir NuGet kaynağı ekleyin.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Açıklama

`dotnet nuget add source`Komut, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.

> [!WARNING]
> Birden çok paket kaynağı eklerken, bir [bağımlılık karışıklık güvenlik açığı](https://aka.ms/pkg-sec-wp)tanıtmamaya dikkat edin.

## <a name="arguments"></a>Bağımsız değişkenler

- **`PACKAGE_SOURCE_PATH`**

  Paket kaynağının yolu.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Kaynağın adı.

- **`-p|--password <PASSWORD>`**

  Kimliği doğrulanmış bir kaynağa bağlanırken kullanılacak parola.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynak kimlik bilgilerinin depolanmasını mümkün.

- **`-u|--username <USER>`**

  Kimliği doğrulanmış bir kaynağa bağlanılırken kullanılacak Kullanıcı adı.

- **`--valid-authentication-types <TYPES>`**

  Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi. `basic`Sunucu ntlm veya anlaşma duyurur ise ve şirket içi Azure DevOps Server BIR Pat kullanırken, kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, bunu olarak ayarlayın. Diğer geçerli değerler,,, ve içerir, `negotiate` `kerberos` `ntlm` `digest` ancak bu değerlerin yararlı olması çok düşüktür.

## <a name="examples"></a>Örnekler

- `nuget.org`Kaynak olarak ekle:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- `c:\packages`Yerel kaynak olarak ekle:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Kimlik doğrulaması gerektiren bir kaynak ekleyin:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Kimlik doğrulaması gerektiren bir kaynak ekleyin (ardından kimlik bilgisi sağlayıcısı 'nı yüklemeye git):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

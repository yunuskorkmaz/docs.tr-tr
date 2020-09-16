---
title: DotNet NuGet güncelleştirme kaynağı komutu
description: DotNet NuGet Update Source komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı güncelleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537860"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget update source` -Bir NuGet kaynağını güncelleştirin.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>Description

`dotnet nuget update source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı güncelleştirir.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password <PASSWORD>`**

  Kimliği doğrulanmış bir kaynağa bağlanırken kullanılacak parola.

- **`-s|--source <SOURCE>`**

  Paket kaynağının yolu.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynak kimlik bilgilerinin depolanmasını mümkün.

- **`-u|--username <USER>`**

  Kimliği doğrulanmış bir kaynağa bağlanılırken kullanılacak Kullanıcı adı.

- **`--valid-authentication-types <TYPES>`**

  Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi. `basic`Sunucu ntlm veya anlaşma duyurur ise ve şirket içi Azure DevOps Server BIR Pat kullanırken, kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, bunu olarak ayarlayın. Diğer geçerli değerler,,, ve içerir, `negotiate` `kerberos` `ntlm` `digest` ancak bu değerlerin yararlı olması çok düşüktür.

## <a name="examples"></a>Örnekler

- Şu ada sahip bir kaynağı güncelleştirin `mySource` :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

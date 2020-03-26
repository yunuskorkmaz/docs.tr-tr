---
title: dotnet nuget güncelleme kaynak komutu
description: Dotnet nuget güncelleştirme kaynak komutu, NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148549"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget güncelleme kaynağı

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget update source`- Bir NuGet kaynağını güncelleştirin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget update source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

- **`-p|--password`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.

- **`-s|--source`**

  Paket kaynağına giden yol.

- **`--store-password-in-clear-text`**

  Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.

- **`-u|--username`**

  Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.

- **`--valid-authentication-types`**

  Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi. Sunucu ntlm veya Negotiate'in reklamını yaparsa ve kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, örneğin şirket içi Azure DevOps Server'a sahip bir PAT kullanırken bunu `basic` ayarlayın. Diğer geçerli `negotiate`değerler `kerberos` `ntlm`, `digest`, , ve , içerir, ancak bu değerlerin yararlı olması olası değildir.

## <a name="examples"></a>Örnekler

- Adı olan bir `mySource`kaynağı güncelleştirin:

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

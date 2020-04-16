---
title: dotnet yardım komutu
description: Dotnet yardım komutu, belirtilen komut için çevrimiçi olarak daha ayrıntılı belgeler gösterir.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463686"
---
# <a name="dotnet-help-reference"></a>dotnet yardım başvurusu

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet help`- Belirtilen komut için daha ayrıntılı belgeleri çevrimiçi olarak gösterir.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet help` docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için başvuru sayfasını açar.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`COMMAND_NAME`**

  .NET Core CLI komutunun adı. Geçerli CLI komutlarının listesi için [CLI komutlarına](index.md#cli-commands)bakın.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- [dotnet yeni](dotnet-new.md) komutu için dokümantasyon sayfasını açar:

  ```dotnetcli
  dotnet help new
  ```

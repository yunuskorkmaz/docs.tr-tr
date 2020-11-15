---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 02/14/2020
ms.openlocfilehash: d583142edabb24df972bdf9a06dbfe04688f9d97
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634474"
---
# <a name="dotnet-help-reference"></a>DotNet yardım başvurusu

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet help` -Belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet help`Komut, docs.Microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.

## <a name="arguments"></a>Arguments

- **`COMMAND_NAME`**

  .NET CLı komutunun adı. Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- [DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:

  ```dotnetcli
  dotnet help new
  ```

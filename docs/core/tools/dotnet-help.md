---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503720"
---
# <a name="dotnet-help-reference"></a>DotNet yardım başvurusu

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet help`-belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.

## <a name="synopsis"></a>Özeti

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet help` komutu, docs.microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`COMMAND_NAME`**

  .NET Core CLI komutunun adı. Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- [DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:

  ```dotnetcli
  dotnet help new
  ```

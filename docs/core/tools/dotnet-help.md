---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 08/08/2019
ms.openlocfilehash: e76f858f2529afc50646473f1aab9d52730cff16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990468"
---
# <a name="dotnet-help-reference"></a>DotNet yardım başvurusu

**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,0 SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Ad

`dotnet help`-Belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.

## <a name="synopsis"></a>Özeti

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet help` Komut, docs.Microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  .NET Core CLI komutunun adı. Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

* [DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:

  ```console
  dotnet help new
  ```

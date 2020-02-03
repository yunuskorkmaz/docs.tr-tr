---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734239"
---
# <a name="dotnet-help-reference"></a>DotNet yardım başvurusu

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Ad

`dotnet help`-belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.

## <a name="synopsis"></a>Özeti

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet help` komutu, docs.microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  .NET Core CLI komutunun adı. Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

* [DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:

  ```dotnetcli
  dotnet help new
  ```

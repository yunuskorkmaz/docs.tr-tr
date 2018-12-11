---
title: DotNet Yardım komutu
description: Belirtilen komut için çevrimiçi belgeleri ayrıntılı dotnet help komutunu gösterir.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168964"
---
# <a name="dotnet-help-reference"></a>DotNet Yardım başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Ad

`dotnet help` -Gösterir, belirtilen komut için çevrimiçi belgeleri daha ayrıntılı.

## <a name="synopsis"></a>Özeti

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet help` Docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için komut başvuru page up açar.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  .NET Core CLI komut adı. Geçerli CLI komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

* İçin belgeler sayfası açılır [yeni dotnet](dotnet-new.md) komutu:

  ```console
  dotnet help new
  ```
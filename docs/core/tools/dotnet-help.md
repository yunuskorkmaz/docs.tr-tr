---
title: DotNet Yardım komutu
description: Belirtilen komut için çevrimiçi belgeleri ayrıntılı dotnet help komutunu gösterir.
ms.date: 12/04/2018
ms.openlocfilehash: 8694494720cdb9a540754fdf79eeb99d5dbe61ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631974"
---
# <a name="dotnet-help-reference"></a>DotNet Yardım başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Ad

`dotnet help` -Gösterir, belirtilen komut için çevrimiçi belgeleri daha ayrıntılı.

## <a name="synopsis"></a>Synopsis

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

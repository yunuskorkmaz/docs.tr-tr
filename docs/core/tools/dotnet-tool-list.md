---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizde yüklü olan .NET araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634291"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool list` -Makinenizde yüklü olan belirtilen türdeki tüm [.net araçlarını](global-tools.md) listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Açıklama

Bu `dotnet tool list` komut, makinenizde yüklü olan tüm .NET genel, araç yolu veya yerel araçları listelemek için bir yol sağlar. Komut, paket adını, yüklü sürümü ve araç komutunu listeler.  Komutunu kullanmak için aşağıdakilerden birini belirtin:

* Varsayılan konumda yüklü olan küresel araçları listelemek için, `--global` seçeneğini kullanın
* Özel bir konumda yüklü olan küresel araçları listelemek için `--tool-path` seçeneğini kullanın.
* Yerel araçları listelemek için `--local` seçeneğini kullanın veya `--global` , `--tool-path` ve seçeneklerini atlayın `--local` .

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="options"></a>Seçenekler

- **`-g|--global`**

  Kullanıcı genelindeki genel araçları listeler. `--tool-path`Seçeneğiyle birleştirilemez. Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--local`**

  Geçerli dizin için yerel araçları listeler. `--global`Veya `--tool-path` seçenekleriyle birleştirilemez. Belirtilmemiş olsa bile, her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler `--local` .

- **`--tool-path <PATH>`**

  Genel araçların bulunacağı bir özel konum belirtir. YOL mutlak veya göreli olabilir. `--global`Seçeneğiyle birleştirilemez. Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.

## <a name="examples"></a>Örnekler

- **`dotnet tool list -g`**

  Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).

- **`dotnet tool list --tool-path c:\global-tools`**

  Belirli bir Windows dizininden küresel araçları listeler.

- **`dotnet tool list --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininden küresel araçları listeler.

- **`dotnet tool list`** veya **`dotnet tool list --local`**

  Geçerli dizinde bulunan tüm yerel araçları listeler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET araçları](global-tools.md)
- [Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma](global-tools-how-to-use.md)
- [Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma](local-tools-how-to-use.md)

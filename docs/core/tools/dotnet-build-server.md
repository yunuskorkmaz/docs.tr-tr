---
title: dotnet build-server komutu
description: Dotnet build-server komutu, bir yapı tarafından başlatılan sunucularla etkileşime girerek etkileşime girer.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463730"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet build-server`- Bir yapı tarafından başlatılan sunucularla etkileşime girerek.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a>Komutlar

- **`shutdown`**

  Dotnet'ten başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucular kapatılır.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--msbuild`**

  MSBuild build sunucusunu kapatır.

- **`--razor`**

  Razor build sunucusunu kapatır.

- **`--vbcscompiler`**

  VB/C# derleyici derleme sunucusunu kapatır.

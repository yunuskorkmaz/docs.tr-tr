---
title: dotnet build-server komutu
description: Dotnet build-server komutu, bir yapı tarafından başlatılan sunucularla etkileşime girerek etkileşime girer.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503784"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet build-server`- Bir yapı tarafından başlatılan sunucularla etkileşime girerek.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
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

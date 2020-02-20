---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503784"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet build-server`-bir derleme tarafından başlatılan sunucularla etkileşime girer.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Komutlar

- **`shutdown`**

  DotNet 'ten başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucular kapanır.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--msbuild`**

  MSBuild yapı sunucusunu kapatır.

- **`--razor`**

  Razor derleme sunucusunu kapatır.

- **`--vbcscompiler`**

  VB/C# derleyici yapı sunucusunu kapatır.

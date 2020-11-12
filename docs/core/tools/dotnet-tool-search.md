---
title: DotNet aracı arama komutu
description: DotNet aracı arama komutu, NuGet.org 'de yayınlanan .NET Core araçlarını arar.
ms.date: 11/11/2020
ms.openlocfilehash: 4357ce4864cad386968e4a76466066fbf2ce4060
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94558076"
---
# <a name="dotnet-tool-search"></a>DotNet aracı araması

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5,0 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool search` -NuGet 'e yayınlanan tüm [.NET Core araçlarını](global-tools.md) arar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a>Description

`dotnet tool search`Komut, .net küresel, araç yolu veya yerel araçlar olarak kullanılabilecek araçlar Için NuGet araması yapmanızı sağlar. Komut, araç adlarını ve başlıklar, açıklamalar ve Etiketler gibi meta verileri arar.

Komut [NuGet arama API](/nuget/api/search-query-service-resource#search-for-packages)'sini kullanır. `packageType=dotnettool`Yalnızca .NET araç paketleri seçmek için üzerine filtreler.

## <a name="options"></a>Seçenekler

- **`--detail`**

  Sorgunun ayrıntılı sonuçlarını gösterir.

- **`--prerelease`**

  Yayın öncesi paketleri içerir.

- **`--skip <NUMBER>`**

  Atlanacak sorgu sonuçlarının sayısını belirtir. Sayfalandırma için kullanılır.

- **`--take <NUMBER>`**

  Gösterilecek sorgu sonuçlarının sayısını belirtir. Sayfalandırma için kullanılır.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="examples"></a>Örnekler

- Paket adı veya açıklamasında "biçim" içeren .NET araçları için arama NuGet.org:

  ```dotnetcli
  dotnet tool search format
  ```

  Çıktı aşağıdaki örneğe benzer şekilde görünür:

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- Paket adı veya meta verilerinde "biçim" olan .NET araçları için arama yapın, yalnızca ilk sonucu gösterin ve ayrıntılı bir görünüm görüntüleyin.

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  Çıktı aşağıdaki örneğe benzer şekilde görünür:

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
- [Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın](local-tools-how-to-use.md)

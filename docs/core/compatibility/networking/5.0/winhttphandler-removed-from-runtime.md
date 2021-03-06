---
title: 'Son değişiklik: WinHttpHandler .NET çalışma zamanından kaldırıldı'
description: .NET 5 ' te WinHttpHandler 'in .NET çalışma zamanından kaldırıldığı Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 95abcfb4d7670be035bd640dbb85458406c1b0e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256419"
---
# <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler .NET çalışma zamanından kaldırıldı

`WinHttpHandler`Sınıf *System.Net.Http.dll* derlemesinden kaldırıldı. Artık yalnızca bant dışı (OOB) [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Net.Http.WinHttpHandler> sınıfı çekirdek .net kitaplıklarının bir parçası olarak kullanılabilir. .NET 5 ' den başlayarak, <xref:System.Net.Http.WinHttpHandler> sınıfı yalnızca ayrı yüklenmiş bir [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

## <a name="recommended-action"></a>Önerilen eylem

[System .net. http. WinHttpHandler NuGet paketini](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)yükler. Ya da, WinHTTP 'ye özgü özellikler gerekmiyorsa, <xref:System.Net.Http.SocketsHttpHandler> bunun yerine kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->

---
title: 'Son değişiklik: WinHttpHandler .NET çalışma zamanından kaldırıldı'
description: .NET 5,0 ' de WinHttpHandler 'in .NET çalışma zamanından kaldırıldığı Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761434"
---
# <a name="winhttphandler-removed-from-net-runtime"></a>.NET çalışma zamanından WinHttpHandler kaldırıldı

`WinHttpHandler`Sınıf *System.Net.Http.dll* derlemesinden kaldırıldı. Artık yalnızca bant dışı (OOB) [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Net.Http.WinHttpHandler> sınıfı çekirdek .net kitaplıklarının bir parçası olarak kullanılabilir. .NET 5,0 ' den başlayarak, <xref:System.Net.Http.WinHttpHandler> sınıfı yalnızca ayrı yüklenmiş bir [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

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

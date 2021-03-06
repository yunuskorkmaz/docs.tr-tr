---
title: 'Son değişiklik: Environment. OSVersion doğru işletim sistemi sürümünü döndürüyor'
description: Core .NET kitaplıklarında .NET 5 ' ün son değişikliği hakkında bilgi edinin. OSVersion, örneğin, uygulama uyumluluğu için seçilen işletim sistemi yerine işletim sisteminin gerçek sürümünü döndürür.
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257537"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion doğru işletim sistemi sürümünü döndürür

<xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür. Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks). MacOS 'ta <xref:System.Environment.OSVersion?displayProperty=nameWithType> temeldeki Darwin çekirdek sürümünü döndürür.

.NET 5 ' den itibaren, <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve macOS için işletim sisteminin gerçek sürümünü döndürür.

Aşağıdaki tabloda davranış farkı gösterilmektedir.

|  | Önceki .NET sürümleri | .NET 5 + |
|--|------------------------|---------|
| Windows | 6.2.9200.0 | 10.0.19042.0 |
| Mac OS | 19.6.0.0 | 10.15.7 |

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler. .NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır. Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur. Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir. Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.

, <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> Ve <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> .NET 5 ' e giriş Ile <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows ve MacOS için tutarlı olacak şekilde değiştirilmiştir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->

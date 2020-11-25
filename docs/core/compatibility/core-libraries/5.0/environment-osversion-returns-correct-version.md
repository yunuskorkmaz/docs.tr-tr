---
title: 'Son değişiklik: Environment. OSVersion doğru işletim sistemi sürümünü döndürüyor'
description: Core .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin. OSVersion, örneğin, uygulama uyumluluğu için seçilen işletim sistemi yerine işletim sisteminin gerçek sürümünü döndürür.
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761723"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion doğru işletim sistemi sürümünü döndürür

<xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür. Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).

.NET 5,0 ' den başlayarak, <xref:System.Environment.OSVersion?displayProperty=nameWithType> işletim sisteminin gerçek sürümünü döndürür.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler. .NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır. Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur. Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir. Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.

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

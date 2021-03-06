---
title: "Son değişiklik: System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmiyor"
description: Şifreleme API 'Lerinin bir tarayıcıda çalıştırıldığında bir özel durum oluşturması durumunda .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 09/16/2020
ms.openlocfilehash: ecbdda4c04642af6b1737e888491eb6565ba7479
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256887"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmez

<xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> bir tarayıcıda çalıştırıldığında bir çalışma zamanı oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde API 'lerin çoğu <xref:System.Security.Cryptography> Blazor WebAssembly uygulamalarında kullanılamaz. .NET 5 ' den başlayarak, Blazor WebAssembly Apps tam .NET 5 API Surface alanını hedeflemelidir, ancak tüm .NET 5 API 'Leri tarayıcı korumalı alan kısıtlamaları nedeniyle desteklenmez. .NET 5 ve sonraki sürümlerinde, desteklenmeyen <xref:System.Security.Cryptography> API 'Ler <xref:System.PlatformNotSupportedException> WebAssembly üzerinde çalışırken bir oluşturur.

> [!TIP]
> [Platform uyumluluk Çözümleyicisi](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) , tarayıcı platformunu destekleyen bir proje oluşturduğunuzda etkilenen API 'lere yapılan tüm çağrıları işaret eder. Bu çözümleyici, .NET 5 ve sonraki uygulamalarda varsayılan olarak çalışır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Microsoft, OpenSSL 'i Blazor WebAssembly yapılandırmasına bir bağımlılık olarak teslim edemiyor. Tarayıcının API 'siyle tümleştirmeye çalışarak bu sorunu geçici olarak çözmek için denedik `SubtleCrypto` . Ne yazık ki, tümleştirme çok zor olan önemli API değişiklikleri gerektirdi.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Şu anda önerecek iyi bir geçici çözüm yoktur.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Security.Cryptography?displayProperty=fullName>Aşağıdakiler hariç tüm API 'ler:

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->

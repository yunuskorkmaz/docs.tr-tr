---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558197"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment. OSVersion doğru işletim sistemi sürümünü döndürür

<xref:System.Environment.OSVersion?displayProperty=nameWithType> uygulama uyumluluğu için seçilen işletim sistemi (örneğin,) yerine, işletim sisteminin gerçek sürümünü (OS) döndürür.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Environment.OSVersion?displayProperty=nameWithType> bir uygulama Windows Uyumluluk modu altında çalıştığında hatalı olabilecek bir işletim sistemi sürümü döndürür. Daha fazla bilgi için bkz. [Getversionexa işlev açıklamaları](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).

.NET 5,0 ' den başlayarak, <xref:System.Environment.OSVersion?displayProperty=nameWithType> işletim sisteminin gerçek sürümünü döndürür.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu özelliğin kullanıcıları, işletim sisteminin gerçek sürümünü döndürmesini bekler. .NET uygulamalarının çoğu uygulama bildiriminde desteklenen sürümlerini belirtmemektedir ve bu nedenle DotNet ana bilgisayardan desteklenen varsayılan sürümü alır. Sonuç olarak, uyumluluk dolgusu çalışan uygulama için nadiren anlamlı olur. Windows yeni bir sürüm yayımlarsa ve daha eski bir DotNet Konağı hala kullanımda olduğunda, bu uygulamalar yanlış bir işletim sistemi sürümü alabilir. Gerçek sürümü döndürmek, geliştiricilerin bu API 'nin beklentileri ile daha fazla satır içidir.

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

İstediğiniz şekilde davrandığından emin olmak için tarafından kullanılan tüm kodları gözden geçirin ve test <xref:System.Environment.OSVersion?displayProperty=nameWithType> edin.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->

---
title: 'Son değişiklik: OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı'
description: Bir önizleme sürümünde sunulan işletim sistemi platformu özniteliklerinin kaldırılmış veya yeniden adlandırılmakta olduğu çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 118c5360eb02c1b4d57fccbd3b2cfdeff0b9fe12
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257264"
---
# <a name="osplatform-attributes-renamed-or-removed"></a>OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı

.NET 5 Preview 8 ' de tanıtılan aşağıdaki öznitelikler kaldırılmıştır veya yeniden adlandırıldı: `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` , ve `ObsoletedInOSPlatformAttribute` .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 Preview 8, ad alanında aşağıdaki öznitelikleri getirdi <xref:System.Runtime.Versioning> :

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

.NET 5 Preview 8 ' de bir proje, gibi bir [hedef çerçeve](../../../../standard/frameworks.md) adı kullanarak .NET 5 ' ın işletim sistemine özgü bir `net5.0-windows` özelliği hedefliyorsa, derleme bir derleme düzeyi `System.Runtime.Versioning.MinimumOSPlatformAttribute` öznitelik ekler.

.NET 5 RC1 'de, `ObsoletedInOSPlatformAttribute` kaldırılmıştır ve `MinimumOSPlatformAttribute` `RemovedInOSPlatformAttribute` aşağıdaki şekilde yeniden adlandırılmıştır:

| Önizleme 8 adı | RC1 ve üzeri adı |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

.NET 5 RC1 ve üzeri sürümlerde, bir proje gibi bir [hedef çerçeve](../../../../standard/frameworks.md) adı kullanarak .NET 5 ' ın işletim sistemine özgü bir `net5.0-windows` özelliğini hedefliyorsa, derleme bir derleme düzeyi <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> öznitelik ekler.

## <a name="reason-for-change"></a>Değişiklik nedeni

.NET 5 Preview 8 ' de <xref:System.Runtime.Versioning> API 'ler için desteklenen platformları belirtmek üzere ' deki öznitelikler sunulmuştur. Öznitelikler, platforma özgü API 'Ler bu API 'Leri desteklemeyen platformlarda kullanılırken derleme uyarıları oluşturmak için [Platform uyumluluk Çözümleyicisi](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) tarafından kullanılır.

.NET 5 RC1 için platform uyumluluk Çözümleyicisi ' ne platform dışlaması için ek bir özellik eklenmiştir. Özelliği, API 'Lerin işletim sistemi platformlarında tamamen desteklenmeyen şekilde işaretlenmesini sağlar. Bu özellik, daha uygun adlar kullanılması da dahil olmak üzere özniteliklerde değişiklikler istendi. `ObsoletedInOSPlatformAttribute`Artık gerekli olmadığından kaldırıldı.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC1

## <a name="recommended-action"></a>Önerilen eylem

Projenizi .NET 5 Preview 8 ' den .NET 5 RC1 'ye yeniden hedeflerken, bu değişiklikler nedeniyle derleme veya çalışma zamanı hatalarıyla karşılaşabilirsiniz. Örneğin, `MinimumOSPlatformAttribute` özniteliği derleme zamanında platforma özgü derlemelere uygulandığından ve eski derleme yapıtlarının hala eskı API adına başvurmasına neden olduğu için, yeniden adlandırmada hata oluşma olasılığı yüksektir.

Örnek derleme zamanı hataları:

- **hata CS0246: ' MinimumOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**
- **hata CS0246: ' RemovedInOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**
- **hata CS0246: ' ObsoletedInOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**

Örnek çalışma zamanı hatası:

**İşlenmeyen özel durum. System. TypeLoadException: ' System. Runtime, Version = 5.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' derlemesinden ' System. Runtime. sürümkodu. MinimumOSPlatformAttribute ' türü yüklenemedi.**

Bu hataları çözmek için:

- Tüm başvurularını güncelleştirin `MinimumOSPlatformAttribute` <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .
- Tüm başvurularını güncelleştirin `RemovedInOSPlatformAttribute` <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .
- Tüm başvuruları kaldırın `ObsoletedInOSPlatformAttribute` .
- Eski derleme yapılarını silmek için projenizi yeniden derleyin (veya temiz + derleme gerçekleştirin).

## <a name="affected-apis"></a>Etkilenen API’ler

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->

---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497796"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs, profil oluşturucular tarafından numaralandırılmıyor

#### <a name="details"></a>Ayrıntılar

.NET Framework v 4.5.1, profil oluşturma API 'SI yanlış bir şekilde <code>RootReferences2()</code> döndürülmez <code>COR_PRF_GC_ROOT_HANDLE</code> ( <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine döndürülür). Bu sorun 4,6 .NET Framework başlayarak düzeltildi.

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

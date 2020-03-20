---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858573"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs profilciler tarafından numaralandırılmıyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework v4.5.1'de profil oluşturma <code>RootReferences2()</code> API'si <code>COR_PRF_GC_ROOT_HANDLE</code> yanlış bir <code>COR_PRF_GC_ROOT_OTHER</code> şekilde asla döndürülmez (bunun yerine döndürülürler). Bu sorun .NET Framework 4.6'dan başlayarak giderilmiştir.|
|Öneri|Bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

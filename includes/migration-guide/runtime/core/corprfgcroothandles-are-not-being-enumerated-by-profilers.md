---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620556"
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

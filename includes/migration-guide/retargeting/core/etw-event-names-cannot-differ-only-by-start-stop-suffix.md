---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614678"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>ETW olay adları yalnızca bir "Başlat" veya "Durdur" sonekiyle farklı olamaz

#### <a name="details"></a>Ayrıntılar

4,6 ve 4.6.1 .NET Framework çalışma zamanı, <xref:System.ArgumentException> Windows için Iki olay izleme (ETW) olay adı yalnızca bir "Başlat" veya "Durdur" sonekiyle farklıysa (bir olay adı `LogUser` ve diğeri adlandırılmışsa olduğu gibi `LogUserStart` ). Bu durumda, çalışma zamanı olay kaynağını oluşturamaz, bu da herhangi bir günlüğe kaydetmeyi yayamaz.

#### <a name="suggestion"></a>Öneri

Özel durumu engellemek için, iki olay adının yalnızca bir "Başlat" veya "Durdur" sonekiyle farklı olmamasını sağlayın. Bu gereksinim, .NET Framework 4.6.2; öğesinden başlayarak kaldırılır; çalışma zamanı, yalnızca "Başlat" ve "Durdur" sonekiyle farklı olay adlarını ayırt edebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

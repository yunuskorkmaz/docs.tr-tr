---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617554"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Dokunmatik özellikli sistemlerde System. Windows. Input. PenContext. Disable için çağrılar bir ArgumentException oluşturabilir

#### <a name="details"></a>Ayrıntılar

Bazı durumlarda, dokunmatik özellikli sistemlerde iç **System. Windows. Int32. PenContext. Disable** yöntemine yapılan çağrılar, yeniden giriş nedeniyle işlenmemiş bir işlem oluşturabilir `T:System.ArgumentException` .

#### <a name="suggestion"></a>Öneri

Bu sorun 4,7 .NET Framework giderilmiştir. Özel durumu engellemek için, .NET Framework .NET Framework 4,7 ' den başlayarak bir sürümüne yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.1       |
| Tür    | Yeniden Hedefleme |

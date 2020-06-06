---
title: Başlangıç ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701521"
---
# <a name="startup-settings-schema"></a>Başlangıç ayarları şeması

Başlangıç ayarları, uygulamayı çalıştırması gereken ortak dil çalışma zamanının sürümünü belirtir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir. Çalışma zamanı sürüm 1,1 ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .|  
|[\<supportedRuntime>](supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|  
|[\<startup>](startup-element.md)|**\<requiredRuntime>** Ve öğelerini içerir **\<supportedRuntime>** .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma dosyası şeması](../index.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

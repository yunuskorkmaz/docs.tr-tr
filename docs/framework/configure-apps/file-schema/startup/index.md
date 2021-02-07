---
description: 'Daha fazla bilgi edinin: başlangıç ayarları şeması'
title: Başlangıç ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: 268b8d8dc2598add61435dd6b07031aa06831737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726097"
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

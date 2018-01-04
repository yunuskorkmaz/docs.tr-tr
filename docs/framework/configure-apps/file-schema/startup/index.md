---
title: "Başlangıç Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0536197d4cb8b30d99f514d8066e94bf84bffdf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="startup-settings-schema"></a>Başlangıç Ayarları Şeması
Başlangıç ayarları uygulama çalışması gerektiğini ortak dil çalışma zamanı sürümünü belirtin.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir. Çalışma zamanı sürüm 1.1 ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|  
|[\<Başlangıç >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|İçeren  **\<requiredRuntime >** ve  **\<supportedRuntime >** öğeleri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)

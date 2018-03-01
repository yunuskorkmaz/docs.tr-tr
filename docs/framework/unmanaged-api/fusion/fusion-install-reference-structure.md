---
title: "FUSION_INSTALL_REFERENCE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36321606fe208233fb6114fe9568b655f0e1b400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE Yapısı
Genel derleme önbelleğinde uygulamanın yüklü olduğu bir derleme bir uygulamanın yaptığı bir başvuru temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbSize`|Yapı bayt cinsinden boyutu.|  
|`dwFlags`|Gelecekteki genişletilebilirliği için ayrılmış. Bu değer, 0 (sıfır) olmalıdır.|  
|`guidScheme`|Başvuru ekler varlık. Bu alan şu değerlerden biri olabilir:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: Derleme Microsoft Windows Installer kullanılarak yüklenmiş bir uygulama tarafından başvuruluyor. `szIdentifier` Alan ayarlanmış `MSI`ve `szNonCanonicalData` alan ayarlanmış `Windows Installer`. Bu düzen Windows yan yana derlemeler için kullanılır.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Derleme görünür bir uygulama tarafından başvurulan **Program Ekle/Kaldır** arabirimi. `szIdentifier` Alanı sağlar uygulama ile kaydeder belirteci **Program Ekle/Kaldır** arabirimi.<br />-FUSION_REFCOUNT_FILEPATH_GUID: Derleme dosya sisteminde bir dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor. `szIdentifier` Alanı, bu dosyanın yolunu sağlar.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: Derleme yalnızca donuk bir dizeyle gösterilen bir uygulama tarafından başvuruluyor. `szIdentifier` Alan bu donuk dize sağlar. Bu değer kaldırdığınızda, Genel Derleme Önbelleği donuk başvuruları varlığını denetlemez.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmıştır.|  
|`szIdentifier`|Genel derleme önbelleğinde derleme yüklü uygulamayı tanımlayan benzersiz bir dize. Değerin değerini bağlıdır `guidScheme` alan.|  
|`szNonCanonicalData`|Yalnızca başvuru ekler varlık tarafından anlaşılan bir dize. Genel Derleme Önbelleği bu dizesi depolar, ancak bunu kullanmaz.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)

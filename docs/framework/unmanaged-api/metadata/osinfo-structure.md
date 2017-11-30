---
title: "OSINFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: OSINFO
api_location: mscoree.dll
api_type: COM
f1_keywords: OSINFO
helpviewer_keywords: OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 700e9bcfe33e5be3725bd24b212b3a77ad139b2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="osinfo-structure"></a>OSINFO Yapısı
Bir derlemeyi ya da modülü için işletim sistemini ayrıntılarını içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows platform işlevi tarafından tanımlanan tanımlayıcı değerlerden biri `GetVersionEx`. Aşağıdaki değerleri desteklenir:<br /><br /> -Microsoft Windows 3.1 belirtmek için VER_PLATFORM_WIN32s, ya 0x0000.<br />-Windows 95, Windows 98 ya da işletim sistemlerini belirtmek için VER_PLATFORM_WIN32_WINDOWS, veya 0x0001, onlardan descended.<br />-Windows NT veya işletim sistemlerini belirtmek için VER_PLATFORM_WIN32_NT, ya da 0x0010, ondan descended.|  
|`dwOSMajorVersion`|İşletim sistemi ana sürüm veya herhangi bir sürümünü belirten bir NULL değer.|  
|`dwOSMinorVersion`|İşletim sistemi alt sürümü veya herhangi bir sürümünü belirten bir NULL değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `OSINFO`dayanır `OSVERSIONINFOEX` yapısı kullanılan Microsoft Windows platform işlev çağrıları `GetVersionEx`. Bu yapı tarafından ASSEMBLYMETADATA yapısı, işletim sistemi desteği göstermek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [Imetadataassemblyemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

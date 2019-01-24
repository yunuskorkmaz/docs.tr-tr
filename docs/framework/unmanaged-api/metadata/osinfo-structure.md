---
title: OSINFO Yapısı
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abab67f28a5fabfc6c348af6b8b502b46510d460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548761"
---
# <a name="osinfo-structure"></a>OSINFO Yapısı
İşletim sistemi için bir derleme veya modül ilgili ayrıntıları içerir.  
  
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
|`dwOSPlatformId`|Microsoft Windows platform işlevi tarafından tanımlanan tanımlayıcısı değerlerinden `GetVersionEx`. Aşağıdaki değerleri desteklenir:<br /><br /> -VER_PLATFORM_WIN32s, veya 0x0000, Microsoft Windows 3.1 belirtmek için.<br />-VER_PLATFORM_WIN32_WINDOWS, veya 0x0001, Windows 95, Windows 98 veya onlardan descended işletim sistemlerini belirtmek için.<br />-VER_PLATFORM_WIN32_NT, veya 0x0010, Windows NT veya ondan descended işletim sistemlerini belirtin.|  
|`dwOSMajorVersion`|İşletim sistemi ana sürümü veya herhangi bir sürümünü belirtmek için bir NULL değer.|  
|`dwOSMinorVersion`|İşletim sistemi alt sürümü veya herhangi bir sürümünü belirtmek için bir NULL değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `OSINFO` dayanır `OSVERSIONINFOEX` yapısı Microsoft Windows platform işlev için kullanılan çağrılar `GetVersionEx`. Bu yapı ASSEMBLYMETADATA yapısı tarafından işletim sistemi desteği belirtmek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

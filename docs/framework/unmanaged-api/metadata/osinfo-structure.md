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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175232"
---
# <a name="osinfo-structure"></a>OSINFO Yapısı
Bir derleme veya modül için işletim sistemi hakkında ayrıntıları içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows platformu işlevi `GetVersionEx`tarafından tanımlanan tanımlayıcı değerlerinden biri. Aşağıdaki değerler desteklenir:<br /><br /> - VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3.1 belirtmek için.<br />- VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya işletim sistemleri bunların indi belirtmek için.<br />- VER_PLATFORM_WIN32_NT veya 0x0002, Windows NT veya işletim sistemleri soyundan belirtmek için.|  
|`dwOSMajorVersion`|İşletim sistemi ana sürümü veya herhangi bir sürümü belirtmek için null değeri.|  
|`dwOSMinorVersion`|İşletim sistemi küçük sürümü veya herhangi bir sürümü belirtmek için null değeri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `OSINFO`Microsoft Windows `OSVERSIONINFOEX` platform işlevine `GetVersionEx`yapılan aramalarda kullanılan yapıya dayanır. Bu yapı, assemblymetadata yapısı tarafından işletim sistemi desteğini belirtmek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
ms.openlocfilehash: ab9d7eb6f5760b43fe805443bbe1ea4a95c72069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501072"
---
# <a name="osinfo-structure"></a>OSINFO Yapısı
Bir derleme veya modül için işletim sistemiyle ilgili ayrıntıları içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows platformu işlevi tarafından tanımlanan tanımlayıcı değerlerinden biri `GetVersionEx` . Aşağıdaki değerler desteklenir:<br /><br /> -VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3,1 belirtmek için.<br />-VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya bunların alt öğelerinden birine ait işletim sistemlerini belirtmek için.<br />-VER_PLATFORM_WIN32_NT veya 0x0002, Windows NT veya bundan sonra gelen işletim sistemlerini belirtmek için.|  
|`dwOSMajorVersion`|İşletim sistemi ana sürümü veya herhangi bir sürümü göstermek için NULL değer.|  
|`dwOSMinorVersion`|İşletim sistemi alt sürümü veya herhangi bir sürümü göstermek için NULL değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `OSINFO`, `OSVERSIONINFOEX` Microsoft Windows platformu işlevi çağrılarında kullanılan yapıya dayalıdır `GetVersionEx` . Bu yapı, ASSEMBLYMETADATA yapısı tarafından, işletim sistemi desteğini göstermek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)

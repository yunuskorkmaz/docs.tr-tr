---
title: COR_PRF_MODULE_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fee786a7acb87598baabed62067b599907bede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599149"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS Numaralandırması
Bir modül özelliklerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Diskten modülü yüklendi.|  
|COR_PRF_MODULE_NGEN|Modül Native Image Generator (Ngen.exe) tarafından oluşturuldu.|  
|COR_PRF_MODULE_DYNAMIC|Modül içindeki yöntemlerde oluşturulduğu <xref:System.Reflection.Emit?displayProperty=nameWithType> ad alanı.|  
|COR_PRF_MODULE_COLLECTIBLE|Modülün ömrü atık toplayıcısı tarafından yönetilir.|  
|COR_PRF_MODULE_RESOURCE|Modül meta veri içeriyor ve yalnızca bir kaynak olarak kullanılır. Bu bit yönetilen eşdeğerdir <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> yöntemi.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Modülün Düzen bellekte düz, eşlenmedi. Bir modül olan bu bit verilirse, taşınabilir yürütülebilir (PE) dosya üst bilgilerinden doğrudan göreli sanal adreslerine (RVA) üst bilgisindeki yorumlarken dikkatli olması gerekir okuma profil oluşturucular.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows çalışma zamanı içerik türü bayrağı meta verilerde, bu modülün derleme için ayarlanır. Tüm Windows meta veri (.winmd) modülleri için durum budur.|  
  
## <a name="remarks"></a>Açıklamalar  
 COR_PRF_MODULE_FLAGS bitten Profil Oluşturucusu'nda dönersiniz `pdwModuleFlags` parametresinin çıktısı [Icorprofilerınfo3::getmoduleınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) yöntemi. İki veya daha fazla bayrakları bazı birleşimleri kullanılabilir, ancak tüm olası birleşimleridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

---
title: "COR_PRF_MODULE_FLAGS Numaralandırması"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 727816a674d2357c8a9ba1f19679c57669e92f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
|COR_PRF_MODULE_DISK|Modül diskten yüklendi.|  
|COR_PRF_MODULE_NGEN|Modülün yerel Görüntü Oluşturucu (Ngen.exe) tarafından oluşturulmuştur.|  
|COR_PRF_MODULE_DYNAMIC|Modül yöntemleri tarafından oluşturulan <xref:System.Reflection.Emit?displayProperty=nameWithType> ad alanı.|  
|COR_PRF_MODULE_COLLECTIBLE|Modülün ömrü atık toplayıcısı tarafından yönetilir.|  
|COR_PRF_MODULE_RESOURCE|Modül meta veri içeriyor ve kesinlikle bir kaynak olarak kullanılır. Bu bit yönetilen eşdeğerdir <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> yöntemi.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Modülün düzeni bellekte düz, eşlenmedi. Bir modül, bu biti ayarlanmış, doğrudan başlığından bilgileri taşınabilir yürütülebilir (PE) dosyası olmasını göreli sanal adresleri (RVAs) üstbilgisindeki yorumlama dikkatli olun okuma profil oluşturucular.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows çalışma zamanı içerik türü bayrağı meta verilerde Bu modülün derleme için ayarlanır. Bu durum Windows Meta veriler (.winmd) olan tüm modülleri için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 COR_PRF_MODULE_FLAGS bitten Profil Oluşturucusu'nda dönersiniz `pdwModuleFlags` parametresinin çıktısı [Icorprofilerınfo3::getmoduleınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) yöntemi. İki veya daha fazla bayrakları bazı birleşimleri mümkündür, ancak tüm olası birleşimleridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

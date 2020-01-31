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
ms.openlocfilehash: 0f6fb469aa9d6d40b762bfd2feec28c28299732f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867119"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS Numaralandırması
Modülün özelliklerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|COR_PRF_MODULE_NGEN|Modül yerel görüntü Oluşturucu (Ngen. exe) tarafından oluşturuldu.|  
|COR_PRF_MODULE_DYNAMIC|Modül, <xref:System.Reflection.Emit?displayProperty=nameWithType> ad alanındaki yöntemlerle oluşturulmuştur.|  
|COR_PRF_MODULE_COLLECTIBLE|Modülün yaşam süresi çöp toplayıcı tarafından yönetiliyor.|  
|COR_PRF_MODULE_RESOURCE|Modül meta veri içermiyor ve kesinlikle kaynak olarak kullanılır. Bu bitin yönetilen eşdeğeri <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> yöntemidir.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Modülün bellekteki yerleşimi düz, eşlenmemiş. Bir modülde bu bit kümesi varsa, profil oluşturucular doğrudan Taşınabilir çalıştırılabilir (PE) dosya başlığından bilgi okuyan, üst bilgide göreli sanal adresleri (RVA) yorumlarken dikkatli olması gerekir.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows Çalışma Zamanı içerik türü bayrağı, Bu modülün derlemesi için meta verilerde ayarlanır. Tüm Windows meta veri (. winmd) modülleri için bu durum budur.|  
  
## <a name="remarks"></a>Açıklamalar  
 COR_PRF_MODULE_FLAGS bitler, [ICorProfilerInfo3:: GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) yönteminin `pdwModuleFlags` output parametresinde profil oluşturucuya döndürülür. İki veya daha fazla bayrak için bazı birleşimler olasıdır, ancak tüm birleşimler mümkün değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)

---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_MODULE_FLAGS numaralandırması'
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
ms.openlocfilehash: 0be5d97bfb6bea069d039d175fc554e0ef59993d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706444"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS Numaralandırması

Modülün özelliklerini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Modül diskten yüklendi.|  
|COR_PRF_MODULE_NGEN|Modül yerel görüntü Oluşturucu (Ngen.exe) tarafından oluşturuldu.|  
|COR_PRF_MODULE_DYNAMIC|Modül, ad alanındaki metotlar tarafından oluşturulmuştur <xref:System.Reflection.Emit?displayProperty=nameWithType> .|  
|COR_PRF_MODULE_COLLECTIBLE|Modülün yaşam süresi çöp toplayıcı tarafından yönetiliyor.|  
|COR_PRF_MODULE_RESOURCE|Modül meta veri içermiyor ve kesinlikle kaynak olarak kullanılır. Bu bitin yönetilen eşdeğeri <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> yöntemidir.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Modülün bellekteki yerleşimi düz, eşlenmemiş. Bir modülde bu bit kümesi varsa, profil oluşturucular doğrudan Taşınabilir çalıştırılabilir (PE) dosya başlığından bilgi okuyan, üst bilgide göreli sanal adresleri (RVA) yorumlarken dikkatli olması gerekir.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Windows Çalışma Zamanı içerik türü bayrağı, Bu modülün derlemesi için meta verilerde ayarlanır. Tüm Windows meta veri (. winmd) modülleri için bu durum budur.|  
  
## <a name="remarks"></a>Açıklamalar  

 COR_PRF_MODULE_FLAGS bitler, `pdwModuleFlags` [ICorProfilerInfo3:: GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) yönteminin çıkış parametresinde profil oluşturucuya döndürülür. İki veya daha fazla bayrak için bazı birleşimler olasıdır, ancak tüm birleşimler mümkün değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)

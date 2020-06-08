---
title: ICorProfilerModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 7a3ad94a4149d6ebb70e077926771e28d7f82779
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494845"
---
# <a name="icorprofilermoduleenumnext-method"></a>ICorProfilerModuleEnum::Next Yöntemi
Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir modül koleksiyonundan belirtilen sayıda bitişik modülü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak modül sayısı.  
  
 `ids`  
 dışı `ModuleID`Her biri alınan bir modülü temsil eden bir değer dizisi.  
  
 `pceltFetched`  
 dışı Dizide gerçekten döndürülen öğe sayısına yönelik bir işaretçi `ids` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt`öğeler döndürüldü.|  
|S_FALSE|Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerModuleEnum Arabirimi](icorprofilermoduleenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)

---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1685b1f739519485e5e68928b29a874587e6f9c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi
Belirtilen alanları bellek numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `callback`  
 [in] Bir işaretçi bir [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonucun hata ayıklayıcı bildirmek için numaralandırılan her bellek bölge için bu yöntem tarafından çağrılan örnek.  
  
 Bir hata geri çağırma gösteriyor olsa bile bellek bölümlerinin listesi devam eder.  
  
 `miniDumpFlags`  
 [in] Kullanılmıyor.  
  
 `clrFlags`  
 [in] Değerini [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) sıralanması bellek bölümlerinin belirtir numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem belirtilen kullanır [Iclrdataenummemoryregionscallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) sonuçları arayan bildirmek için örneği.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRDataEnumMemoryRegions Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)

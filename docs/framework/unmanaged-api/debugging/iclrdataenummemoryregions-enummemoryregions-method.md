---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860693"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions Yöntemi
Belirtilen bellek alanını numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `callback`  
 'ndaki Bir [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğine, sonucun hata ayıklayıcısını bildirmek üzere numaralandırılmakta olan her bellek bölgesi için bu yöntem tarafından çağrılan bir işaretçi.  
  
 Geri arama bir hata gösteriyorsa bile, bellek bölümlerinin numaralandırılması devam eder.  
  
 `miniDumpFlags`  
 'ndaki Kullanılmıyor.  
  
 `clrFlags`  
 'ndaki Numaralandırılacak bellek bölgelerini belirten [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, sonuçları çağırana bildirmek için belirtilen [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) örneğini kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataEnumMemoryRegions Arabirimi](iclrdataenummemoryregions-interface.md)

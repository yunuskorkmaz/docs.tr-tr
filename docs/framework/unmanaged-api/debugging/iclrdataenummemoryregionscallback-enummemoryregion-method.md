---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: e4fa0a3745200d39a468292e9520b1aeb0e9f1b2
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860674"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Yöntemi
Hata ayıklayıcıya raporlamak için [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) tarafından çağırılır, belirtilen bellek bölgesini numaralandırma girişimi sonucu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Numaralandırılacak bellek bölgesinin başlangıç adresi.  
  
 `size`  
 'ndaki Bellek bölgesinin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi `ICLRDataEnumMemoryRegions::EnumMemoryRegions` , her bir bellek bölgesini numaralandırma denemesinden sonra bu geri çağırma yöntemini çağırır. Bu yöntem hata belirten bir HRESULT döndürürse bile sabit listesi devam edecektir.  
  
 Bu geri çağırma tarafından bildirilen bölgeler, yinelemeler veya çakışan bölgeler olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataEnumMemoryRegionsCallback Arabirimi](iclrdataenummemoryregionscallback-interface.md)

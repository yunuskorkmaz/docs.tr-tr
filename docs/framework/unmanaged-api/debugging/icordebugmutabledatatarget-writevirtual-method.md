---
title: "ICorDebugMutableDataTarget::WriteVirtual yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 303c5737ebd241b8f2f756de0ed5426787de3bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual yöntemi
Bellek, hedef işlem adres alanı yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] İçeriğini yazılacak adresinde `pBuffer`.  
  
 `pBuffer`  
 [in] Yazılacak baytları içeren bir bayt dizisine bir işaretçi.  
  
 `address`  
 [in] Bayt sayısı `pBuffer`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Başarı veya diğer `HRESULT` hatasında.  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm bayt yazılamaz yöntem çağrısının hedef adres alanındaki tüm bayt değiştirmeden başarısız olur. (Aksi halde, hedef daha yapar tutarsız bir durumda güvenilir hata ayıklama.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

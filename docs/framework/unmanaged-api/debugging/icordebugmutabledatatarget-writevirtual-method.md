---
title: ICorDebugMutableDataTarget::WriteVirtual yöntemi
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417420"
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
 `S_OK` Başarı veya diğer `HRESULT` hatasında.  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm bayt yazılamaz yöntem çağrısının hedef adres alanındaki tüm bayt değiştirmeden başarısız olur. (Aksi halde, hedef daha yapar tutarsız bir durumda güvenilir hata ayıklama.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

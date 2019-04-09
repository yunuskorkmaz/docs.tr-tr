---
title: ICorDebugMutableDataTarget::WriteVirtual yöntemi
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171658"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual yöntemi
Bellek, hedef işlemin adres alanına yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 [in] İçeriğini yazılacağı adresindeki `pBuffer`.  
  
 `pBuffer`  
 [in] Yazılacak baytları içeren bir bayt dizisine bir işaretçi.  
  
 `address`  
 [in] Bayt sayısı `pBuffer`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` Başarı veya diğer `HRESULT` başarısız.  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir bayt yazılamaz yöntem çağrısında hedef adres alanındaki tüm bayt değiştirmeden başarısız olur. (Aksi takdirde, hedef daha yapar tutarsız bir durumda güvenilir hata ayıklama.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

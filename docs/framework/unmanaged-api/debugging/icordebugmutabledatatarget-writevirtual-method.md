---
title: 'Icordebugmutabledatatarget:: WriteVirtual yöntemi'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792827"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>Icordebugmutabledatatarget:: WriteVirtual yöntemi
Belleği hedef işlem adres alanına yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki `pBuffer`içeriğinin yazılacağı adres.  
  
 `pBuffer`  
 'ndaki Yazılacak baytları içeren bir bayt dizisine yönelik bir işaretçi.  
  
 `address`  
 'ndaki `pBuffer`bayt sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 başarılı veya hata durumunda başka bir `HRESULT` `S_OK`.  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir bayt yazılamaz ise, yöntem çağrısı, hedef adres alanındaki herhangi bir bayt değiştirilmeden başarısız olur. (Aksi halde, hedef, güvenli olmayan bir şekilde hata ayıklama olanağı sunan tutarsız bir durumda olabilir.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

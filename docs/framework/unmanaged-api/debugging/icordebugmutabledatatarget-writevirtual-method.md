---
description: ': Icordebugmutabledatatarget:: WriteVirtual yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmutabledatatarget:: WriteVirtual yöntemi'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 3f3400456b7af51f4b24d7e14e35d641f03a8bfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637826"
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
 'ndaki İçeriğin yazılacağı adres `pBuffer` .  
  
 `pBuffer`  
 'ndaki Yazılacak baytları içeren bir bayt dizisine yönelik bir işaretçi.  
  
 `address`  
 'ndaki İçindeki bayt sayısı `pBuffer` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` başarılı veya `HRESULT` başarısız olduğunda.  
  
## <a name="remarks"></a>Açıklamalar  

 Herhangi bir bayt yazılamaz ise, yöntem çağrısı, hedef adres alanındaki herhangi bir bayt değiştirilmeden başarısız olur. (Aksi halde, hedef, güvenli olmayan bir şekilde hata ayıklama olanağı sunan tutarsız bir durumda olabilir.)  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

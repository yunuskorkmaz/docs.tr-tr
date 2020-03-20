---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179043"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>ICorDebugAppDomain4::GetObjectForCCW Metodu
Yönetilen bir nesneyi COM çağrılabilir sarıcı (CCW) işaretçisinden alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ccwPointer`  
 [içinde] Com çağrılabilir sarıcı (CCW) işaretçisi.  
  
 `ppManagedObject`  
 [çıkış] Verilen CCW işaretçisine karşılık gelen yönetilen nesneyi temsil eden bir "ICorDebugValue" nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAppDomain4 Arabirimi](icordebugappdomain4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

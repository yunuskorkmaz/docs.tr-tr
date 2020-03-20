---
title: ICorDebugDataTarget2::GetImageFromPointer Yöntemi
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178914"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a>ICorDebugDataTarget2::GetImageFromPointer Yöntemi
Modül taban adresini ve boyutunu o modüldeki bir adresten döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `addr`  
 Modüldeki bir adresi temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.  
  
 `pImageBase`  
 [çıkış] Modülün temel adresini temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.  
  
 `pSize`  
 Modül boyutuna bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget2 Arabirimi](icordebugdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

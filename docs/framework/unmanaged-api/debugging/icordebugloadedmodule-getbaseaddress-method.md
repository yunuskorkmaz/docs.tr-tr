---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5ef73be22ea79d15ec53e8ab33c34441002acce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732433"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a>ICorDebugLoadedModule::GetBaseAddress Metodu
Yüklenen bir modülün temel adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAddress`  
 [out] Yüklenen bir modülün taban adresi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugLoadedModule Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

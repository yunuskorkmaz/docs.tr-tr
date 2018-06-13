---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413237"
---
# <a name="icordebugloadedmodulegetsize-method"></a>ICorDebugLoadedModule::GetSize Metodu
Yüklenen modülün bayt cinsinden boyutu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcBytes`  
 [out] Yüklenen modülün bayt sayısını gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugLoadedModule Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

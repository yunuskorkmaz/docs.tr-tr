---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111273"
---
# <a name="icordebugloadedmodulegetname-method"></a>ICorDebugLoadedModule::GetName Yöntemi
Yüklenen bir modülün adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Karakter sayısı `szName` arabellek.  
  
 `pcchName`  
 [out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.  
  
 `szName`  
 [out] Yüklenen bir modülün adını içeren bir karakter dizisi.  
  
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

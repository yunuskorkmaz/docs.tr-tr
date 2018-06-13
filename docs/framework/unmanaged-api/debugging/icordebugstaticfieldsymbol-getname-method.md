---
title: ICorDebugStaticFieldSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095c84a5cb448803bbfa45e0fad8a494343ca7f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422324"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a>ICorDebugStaticFieldSymbol::GetName yöntemi
Statik alanın adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Karakter sayısını `szName` arabellek.  
  
 `pcchName`  
 [out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.  
  
 `szName`  
 [out] Döndürülen adını depolar bir karakter dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugStaticFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

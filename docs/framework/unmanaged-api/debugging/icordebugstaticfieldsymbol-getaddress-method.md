---
description: ': ICorDebugStaticFieldSymbol:: GetAddress yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugStaticFieldSymbol:: GetAddress Yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 1944839ff6afc31dc3667111397cbb088b95b412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801013"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a>ICorDebugStaticFieldSymbol:: GetAddress Yöntemi

Statik bir alanın adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 pRVA  
 dışı Statik alanın göreli sanal adresine (RVA) yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStaticFieldSymbol Arabirimi](icordebugstaticfieldsymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936869"
---
# <a name="icordebugloadedmodulegetsize-method"></a>ICorDebugLoadedModule::GetSize Metodu
Yüklenen modülün bayt cinsinden boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pcBytes`  
 dışı Yüklenen modüldeki bayt sayısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugLoadedModule Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

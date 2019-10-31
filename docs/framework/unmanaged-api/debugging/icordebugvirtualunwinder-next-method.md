---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: ed80b7a630f78002ded14a1bec206cc8712bd504
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121856"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next yöntemi
Çağıranın bağlamına ilerletir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 geriye doğru bir şekilde oluştuysa veya daha fazla çerçeve olmadığından geriye doğru izleme `S_OK` `CORDBG_S_AT_END_OF_STACK`.  
  
 Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri `CORDBG_E_DATA_TARGET_ERROR`döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın denetçisi ilerlemesinin devam ettiğinden emin olunması gerekir, böylece sonuç olarak bir `Next` çağrısı, başarısız bir HRESULT veya `CORDBG_S_AT_END_OF_STACK`döndürmeyecektir. Sonsuza kadar `S_OK` döndürme sonsuz döngüye neden olabilir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

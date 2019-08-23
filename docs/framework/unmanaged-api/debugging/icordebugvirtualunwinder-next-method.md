---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967929"
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
 `S_OK`geriye doğru izleme işlemi başarılı olduysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru tamamlanamıyor.  
  
 Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri `CORDBG_E_DATA_TARGET_ERROR`döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın denetçisi ilerlemeye devam ettiğinden emin olunması gerekir, bu yüzden bir çağrısının `Next` başarısız bir HRESULT veya `CORDBG_S_AT_END_OF_STACK`geri dönmesi gerekir. Süresiz `S_OK` olarak döndürmek sonsuz döngüye neden olabilir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

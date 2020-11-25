---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: bfc827a1503b0367a442e3f3ca0915bd2aaeb01e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725956"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next yöntemi

Çağıranın bağlamına ilerletir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parametreler  

 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` geriye doğru izleme işlemi başarılı olduysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru tamamlanamıyor.  
  
 Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri döndürülür `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Açıklamalar  

 Yığın denetçisi ilerlemeye devam ettiğinden emin olunması gerekir, bu yüzden bir çağrısının `Next` başarısız BIR HRESULT veya geri dönmesi gerekir `CORDBG_S_AT_END_OF_STACK` . Süresiz olarak döndürmek `S_OK` sonsuz döngüye neden olabilir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790813"
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

- [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

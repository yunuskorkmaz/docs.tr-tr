---
title: ICorDebugVirtualUnwinder::Next yöntemi
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4bacbd9ef11f6f6cb6d9952290c00f1b8ce50aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423435"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next yöntemi
Çağıranın içeriği ilerler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` bırakma başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve yok olduğundan bırakma tamamlanamazsa.  
  
 Döndürülen HRESULT başarısız, Icordebug API'leri döndürür, `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın walker, ilerleme, sonuç olarak bu kılar emin olmalısınız yapılan bir çağrı `Next` başarısız döndürülecek HRESULT veya `CORDBG_S_AT_END_OF_STACK`. Döndürme `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: "ICorDebugVirtualUnwinder::Next yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61f7e5afc65019f1817b15ae84ca3f7b42e3ece9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 `S_OK`bırakma başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve yok olduğundan bırakma tamamlanamazsa.  
  
 Döndürülen HRESULT başarısız, Icordebug API'leri döndürür, `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın walker, ilerleme, sonuç olarak bu kılar emin olmalısınız yapılan bir çağrı `Next` başarısız döndürülecek HRESULT veya `CORDBG_S_AT_END_OF_STACK`. Döndürme `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

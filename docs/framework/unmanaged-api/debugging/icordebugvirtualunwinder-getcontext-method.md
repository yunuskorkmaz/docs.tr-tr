---
title: "ICorDebugVirtualUnwinder::GetContext yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d034016c7470cbf134cb142db9f98d82d0c59d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext yöntemi
Bu unwinder geçerli bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `contextFlags`  
 [in] Hangi kısımlarının (WinNT.h içinde tanımlanan) dönmek için bağlamı belirtmek bayraklar.  
  
 `cbContextBuf`  
 [in] Bayt sayısı `contextBuf`.  
  
 `contextSize`  
 [out] Gerçekte yazılan bayt sayısı için bir işaretçi `contextBuf`.  
  
 `contextBuf`  
 [out] Bu unwinder geçerli içeriği içeren bir bayt dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tüm mscordbi tarafından alınan HRESULT değer başarısız önemli kabul edilir ve Icordebug dönmek API neden olacak `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
 Başlangıç değerini ayarlamak `contextBuf` bağımsız değişkeni çağrılarak döndürülen bağlamı arabelleğinde [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemi.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
 Unwinding may yalnızca geri yükleme bir alt yazmaçların geçici olmayan gibi yalnızca kaydeder olduğundan, bağlam tam kayıt durumu gerçek yöntem çağrısının aynı anda aynı olmayabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

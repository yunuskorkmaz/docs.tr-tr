---
title: ICorDebugVirtualUnwinder::GetContext yöntemi
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8377c374ae71c45cf198446d66a5f9a235a2142f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775367"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext yöntemi
Bu unwinder geçerli bağlamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `contextFlags`  
 [in] Hangi parçalarının (WinNT.h içinde tanımlanan) dönmek bağlamının belirten bayraklar.  
  
 `cbContextBuf`  
 [in] Bayt sayısı `contextBuf`.  
  
 `contextSize`  
 [out] Gerçekte yazılan bayt sayısı için bir işaretçi `contextBuf`.  
  
 `contextBuf`  
 [out] Bu unwinder geçerli bağlamını içeren bir bayt dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tüm önemli kabul edilir ve Icordebug döndürülecek API'leri neden olacak mscordbi tarafından alınan HRESULT değerini başarısız `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
 Başlangıç değeri ayarlamak `contextBuf` bağımsız değişkeni çağrılarak döndürülen bağlamı arabelleğine [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemi.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
 Yalnızca geriye doğru Mayıs yalnızca geri yükleme bulmasına geçici olmayan gibi yazmaçların kaydeder olduğundan, bağlamı tam olarak zaman gerçek bir yöntem çağrısının kayıt durumu eşleşmeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugStackWalk::GetContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba1e6c113fb4caa0db8963e238d3eceba0cc8ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224864"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext Yöntemi
Geçerli kare bağlamını döndürür [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `contextFlags`  
 [in] İstenen içeriği (WinNT.h içinde tanımlanmıştır) bağlam arabellek belirten bayraklar.  
  
 `contextBufSize`  
 [in] Ayrılmış bağlam arabellek boyutu.  
  
 `contextSize`  
 [out] Bağlam gerçek boyutu. Bu değer, ya da bağlam arabellek boyutu eşit olmalıdır.  
  
 `contextBuf`  
 [out] İçerik arabelleği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Geçerli çerçevenin içeriği başarıyla döndürüldü.|  
|E_FAIL|Bağlam döndürülemedi.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)|Bağlam arabellek çok küçük.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisini yığının sonuna bulunur. Bu nedenle, hiçbir ek çerçeveler erişilebilir.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Geriye doğru izleme yalnızca bir alt yazmaçların geçici olmayan kayıtlar gibi geri yükler için bağlam aramanın zaman tam olarak kayıt durumu eşleşmeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

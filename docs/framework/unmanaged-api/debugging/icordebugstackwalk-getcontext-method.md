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
ms.openlocfilehash: 700e0af05828b9fe0a50c1aac114e840adc276b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131845"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext Yöntemi
[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesindeki geçerli karenin bağlamını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `contextFlags`  
 'ndaki Bağlam arabelleğinin istenen içeriğini belirten bayraklar (WinNT. h içinde tanımlanmıştır).  
  
 `contextBufSize`  
 'ndaki Bağlam arabelleğinin ayrılan boyutu.  
  
 `contextSize`  
 dışı Bağlamın gerçek boyutu. Bu değer, bağlam arabelleğinin boyutundan küçük veya buna eşit olmalıdır.  
  
 `contextBuf`  
 dışı Bağlam arabelleği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Geçerli çerçevenin bağlamı başarıyla döndürüldü.|  
|E_FAıL|Bağlam döndürülemedi.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT BUFFER)|Bağlam arabelleği çok küçük.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Geriye doğru kaldırma, geçici olmayan Yazmaçları gibi yazmaçların yalnızca bir alt kümesini geri yüklediği için, bağlam çağrı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 1f5b413ffbbc8fccbea38f23d8c87d40e010dd37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130610"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi
Hata ayıklayıcısını, ortak dil çalışma zamanı modülü simgelerinin değiştiği hakkında bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Simgenin değiştiği modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pModule`  
 'ndaki Simgelerin değiştiği modülü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.  
  
 `pSymbolStream`  
 'ndaki Değiştirilen sembolleri içeren Win32 COM `IStream` nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [ıvmunmanagedreader:: UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [ıımunmanagedreader:: Synccesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)çağırarak hata ayıklayıcının bir modülün sembol görünümünü güncelleştirme fırsatı sağlar.  
  
 Bu geri çağırma aynı modül için birden çok kez gerçekleşebilir.  
  
 Bir hata ayıklayıcı, ilişkisiz kaynak düzeyinde kesme noktaları bağlamayı denemelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: 9ee6f43c94b8ff2e765d2a0dde0697c4c895a94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212379"
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
 'ndaki Değiştirilen sembolleri içeren bir Win32 COM `IStream` nesnesi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [ıvmunmanagedreader:: UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [ıımunmanagedreader:: Synccesymbolstore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md)çağırarak hata ayıklayıcının bir modülün sembol görünümünü güncelleştirme fırsatı sağlar.  
  
 Bu geri çağırma aynı modül için birden çok kez gerçekleşebilir.  
  
 Bir hata ayıklayıcı, ilişkisiz kaynak düzeyinde kesme noktaları bağlamayı denemelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)

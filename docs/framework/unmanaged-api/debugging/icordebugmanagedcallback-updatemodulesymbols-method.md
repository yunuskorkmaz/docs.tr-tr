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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581ea4f974bfec3961a32cd7c9985a5e45d2bddd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209989"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi
Hata ayıklayıcı ortak dil çalışma zamanı modülü için Sembol değiştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Hangi simgelerin değişmiş modülü içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pModule`  
 [in] Modül, semboller değiştirildi temsil eden bir Icordebugmodule nesne işaretçisi.  
  
 `pSymbolStream`  
 [in] Bir Win32 COM işaretçisi `IStream` değiştirilmiş simgeleri içeren nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcı'nın bir modülün sembolleri görünümünü çağırarak güncelleştirmek için bir fırsat sağlar. [Isymunmanagedreader::updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [Isymunmanagedreader::replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Bu geri çağırma aynı modülü için birden çok kez gerçekleşebilir.  
  
 Bir hata ayıklayıcı ilişkisiz kaynak düzeyinde kesme noktaları bağlama çalışmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

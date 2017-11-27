---
title: "ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UpdateModuleSymbols
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a1606c256bbfd3b0a7de29b84aace1b4831a016
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols Yöntemi
Hata ayıklayıcı bir ortak dil çalışma zamanı modülü simgelerini değişmiş bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye simgeleri değiştirilmesi modülü içeren uygulama etki alanını temsil eder.  
  
 `pModule`  
 [in] Bir işaretçi Icordebugmodule nesneye simgeleri değiştirilmesi modülü temsil eder.  
  
 `pSymbolStream`  
 [in] Bir işaretçi bir Win32 COM `IStream` değiştirilmiş sembolleri içeren nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem çağırarak bir modülün simgelerin Hata Ayıklayıcı'nın Görünümü güncelleştirmek için bir fırsat sunar [Isymunmanagedreader::updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) veya [Isymunmanagedreader::replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Bu geri çağırma birden çok kez aynı modülü için oluşabilir.  
  
 Bir hata ayıklayıcısı ilişkisiz kaynak düzeyi kesme noktaları bağlamak denemelisiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugmanagedcallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

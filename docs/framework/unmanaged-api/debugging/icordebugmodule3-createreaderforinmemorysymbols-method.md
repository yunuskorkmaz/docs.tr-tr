---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2838c6c1fe8641e343fac1a3efa82a39ee177abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi
Dinamik bir modül için bir hata ayıklama simgesi okuyucu oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Parametreler  
 nRIID  
 [in] Döndürülecek COM arabirimi IID. Genel olarak, bir [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Döndürülen arayüzü için bir işaretçi işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Okuyucu başarıyla oluşturuldu.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modül bir bellek içi ya da dinamik modül değil.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Simge uygulama tarafından sağlanan yok veya henüz kullanılabilir değil.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Okuyucu oluşturulamadı.  
  
## <a name="remarks"></a>Açıklamalar  
 Simgeler ilk kullanılabilir olduktan sonra bu yöntem de bellek içi (dinamik olmayan) modülleri için bir simge Okuyucu nesnesi oluşturmak için kullanılan, ancak yalnızca olabilir (belirttiği [UpdateModuleSymbols yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırma).  
  
 Bu yöntem her çağrıldığında yeni bir okuyucu örneği döndürür (gibi [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)). Bu nedenle, hata ayıklayıcı sonucu önbelleğe alınması ve temel alınan veri yalnızca değişmiş olabilir zaman yeni bir örneğini iste (diğer bir deyişle, bir [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri alındığında).  
  
 İlk tür yüklenen kadar dinamik modüllerdeki semboller kullanılabilir gerekmez (belirtildiği gibi [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırma).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e404228cbc6efb81ed90c135358b1832ddcd8954
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185371"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi
Dinamik modül için hata ayıklama simge okuyucu oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Parametreler  
 riid  
 [in] Döndürülecek COM arabirimi Laboratuvardaki. Bu genellikle bir [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Döndürülen arabirim işaretçisi için işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Okuyucu başarıyla oluşturuldu.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modül, bellek veya dinamik bir modül değil.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Simgeleri uygulama tarafından sağlanan değil veya henüz kullanıma sunulmamıştır.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Okuyucusu oluşturulamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Simgeleri ilk kullanılabilir olduktan sonra bu yöntem aynı zamanda bir bellek içi (dinamik olmayan) modüller için Sembol Okuyucu nesnesi oluşturmak için kullanılan, ancak yalnızca olabilir (belirttiği [UpdateModuleSymbols yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırma).  
  
 Her çağrıldığında bu yöntem, yeni bir okuyucu örneği döndürür. (gibi [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Hata ayıklayıcı bu nedenle, ve sonuç önbellek ister yeni bir örneği temel alınan verileri yalnızca değişmiş olabilir (diğer bir deyişle, bir [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri alındığında).  
  
 Dinamik modüller kadar ilk türü yüklenmiş olan simgeleri kullanılabilir gerekmez (gösterildiği gibi [LoadClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırma).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

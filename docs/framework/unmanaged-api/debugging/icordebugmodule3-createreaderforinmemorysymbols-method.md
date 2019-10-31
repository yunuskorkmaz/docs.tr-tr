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
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137310"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi
Dinamik bir modül için hata ayıklama simgesi okuyucu oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parametreler  
 riıd  
 'ndaki Döndürülecek COM arabiriminin IID 'si. Genellikle bu bir [ıstreamunmanagedreader arabirimidir](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Okuyucu başarıyla oluşturuldu.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modül, bellek içi veya dinamik bir modül değil.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Simgeler uygulama tarafından sağlanmadı veya henüz kullanılamıyor.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 Okuyucu oluşturulamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bellek içi (dinamik olmayan) modüller için bir sembol okuyucu nesnesi oluşturmak için de kullanılabilir, ancak yalnızca semboller önce kullanılabilir olduktan sonra ( [UpdateModuleSymbols yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) geri çağırması tarafından gösterilir).  
  
 Bu yöntem, her çağrılışında yeni bir okuyucu örneği döndürür ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)gibi). Bu nedenle, hata ayıklayıcı sonucu önbelleğe almalıdır ve yalnızca temeldeki veriler değiştiği zaman yeni bir örnek ister (yani, bir [LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırması alındığında).  
  
 Dinamik modüller, ilk tür yükleninceye kadar kullanılabilir simgelere sahip değildir ( [LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) geri çağırması tarafından belirtildiği gibi).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

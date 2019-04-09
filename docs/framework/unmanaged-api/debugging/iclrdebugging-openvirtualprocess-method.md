---
title: ICLRDebugging::OpenVirtualProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122583"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess Yöntemi
Ortak dil çalışma zamanı (CLR) modül işleme yüklendiğinde karşılık gelen Icordebugprocess arabirimi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleBaseAddress`  
 [in] Hedef işlemde bir modülün temel adres. Belirtilen modül bir CLR modülünü değilse COR_E_NOT_CLR döndürülür.  
  
 `pDataTarget`  
 [in] İşlem durumu denetlemek yönetilen hata ayıklayıcı sağlayan veri hedef özeti. Hata ayıklayıcı uygulamalıdır [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi. Uygulamalıdır [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) ayıklanmakta olan CLR yüklü olmayan yerel bilgisayarda senaryoları desteklemek için arabirim.  
  
 `pLibraryProvider`  
 [in] Ve yüklenecek üzerine yerleştirilecek sürümüne özel hata ayıklama kitaplıklarına izin veren bir kitaplık sağlayıcı geri arama arabirimi. Bu parametre yalnızca gereklidir `ppProcess` veya `pFlags` değil `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] Bu hata ayıklayıcı hata ayıklaması yapabilirsiniz CLR en yüksek sürümü. Ana, alt, belirtin ve bu hata ayıklayıcı destekleyen en son CLR sürümü sürümlerinden yapı ve düzeltme numarası 65535 hizmet sürümlerini gelecekteki yerinde CLR uyum sağlayacak şekilde ayarlayın.  
  
 `riidProcess`  
 [in] Alınacak Icordebugprocess arabirimi kimliği. Şu anda, kabul edilen değerler yalnızca IID_CORDEBUGPROCESS3 IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS ' dir.  
  
 `ppProcess`  
 [out] Bir işaretçi tarafından tanımlanan COM arabirimi `riidProcess`.  
  
 `pVersion`  
 [out içinde] CLR sürümü. Bu değer, giriş olabilir `null`. Bu da işaret edebilir bir [clr_debuggıng_versıon](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) yapısı, bu durumda yapısı `wStructVersion` alan 0 (sıfır) başlatılması gerekir.  
  
 Çıktıda, döndürülen `CLR_DEBUGGING_VERSION` yapısı, CLR sürüm bilgilerini oturum doldurulur.  
  
 `pdwFlags`  
 [out] Belirtilen çalışma zamanı hakkında bilgi bayrakları. Bkz: [clr_debuggıng_process_flags](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) konu bayrakları açıklaması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pDataTarget` olan `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) geri çağırma bir hata döndürür veya geçerli bir tanıtıcı sağlamaz.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` çalışma zamanının bu sürümü için gerekli verileri hedef arabirimi uygulamıyor.|  
|CORDBG_E_NOT_CLR|Belirtilen modül bir CLR modülünü değil. Bir CLR modül bellek bozulmuş, modül kullanılabilir olmadığı veya CLR sürümünün dolgu sürümden daha sonraki algılanamıyor olduğunda bu HRESULT da döndürülür.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Bu çalışma zamanı sürümü, bu hata ayıklama modelini desteklemiyor. Şu anda, hata ayıklama modeli önce CLR sürümleri tarafından desteklenmeyen [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Çıkış parametresi doğru değer yine de bu hatadan sonra ayarlanır.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Bu hata ayıklayıcı desteği iddia sürümünden büyük CLR sürümüdür. `pwszVersion` Çıkış parametresi doğru değer yine de bu hatadan sonra ayarlanır.|  
|E_NO_INTERFACE|`riidProcess` Arabirimi kullanılabilir değil.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Yapısı için tanınan bir değer yok `wStructVersion`. Şu anda yalnızca kabul edilen değeri 0'dır.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

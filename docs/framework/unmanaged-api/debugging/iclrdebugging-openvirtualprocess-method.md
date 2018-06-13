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
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408258"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess Yöntemi
Bir ortak dil çalışma zamanı (CLR) modülü işleminde yüklenen karşılık gelen Icordebugprocess arabirimi alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `moduleBaseAddress`  
 [in] Hedef işlemin modülünde temel adres. Belirtilen modül CLR modül değilse COR_E_NOT_CLR döndürülür.  
  
 `pDataTarget`  
 [in] İşlem durumu denetlemek yönetilen hata ayıklayıcı sağlayan veri hedef özeti. Hata ayıklayıcı uygulamalıdır [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi. Uygulamanız gerekir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , ayıklanacak CLR yüklü olmayan yerel bilgisayarda senaryoları desteklemek için arabirim.  
  
 `pLibraryProvider`  
 [in] Sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olmasını sağlayan bir kitaplığı sağlayıcısı geri çağırma arabirimi. Bu parametre yalnızca gerekli ise `ppProcess` veya `pFlags` değil `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] Bu hata ayıklayıcı ayıklayabilirsiniz CLR yüksek sürümü. Ana, ikincil, belirtin ve bu hata ayıklayıcı destekleyen en son CLR sürümü sürümlerden yapı ve düzeltme numarası 65535 sürümleri bakım gelecekteki yerinde CLR uyum sağlayacak şekilde ayarlayın.  
  
 `riidProcess`  
 [in] Alınacak Icordebugprocess arabirimi kimliği. Şu anda, kabul edilen değerler yalnızca IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS ' dir.  
  
 `ppProcess`  
 [out] Tarafından tanımlanan COM arabirimi için bir işaretçi `riidProcess`.  
  
 `pVersion`  
 [içinde out] CLR sürümü. Giriş, bu değer olabilir `null`. Bu da işaret edebilir bir [clr_debuggıng_versıon](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) yapısı, bu durumda yapısı `wStructVersion` alan 0 (sıfır) başlatılmalıdır.  
  
 Çıktıyı, döndürülen `CLR_DEBUGGING_VERSION` yapısı, CLR sürüm bilgileri ile doldurulur.  
  
 `pdwFlags`  
 [out] Belirtilen çalışma zamanı hakkında bilgi bayraklar. Bkz: [clr_debuggıng_process_flags](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) konu bayrakları açıklaması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pDataTarget` olan `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) geri çağırma bir hata döndürür veya geçerli bir tanıtıcı sağlamaz.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` çalışma zamanı bu sürümü için gerekli verileri hedef arabirimleri uygulamıyor.|  
|CORDBG_E_NOT_CLR|Belirtilen modül bir CLR modül değil. Bir CLR modül bozuk belleği, modülü kullanılamıyor veya CLR sürümü dolgusu sürümünden daha yeni olduğundan algılanamıyor olduğunda bu HRESULT da döndürülür.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Bu çalışma zamanı sürümü bu hata ayıklama modelini desteklemiyor. Şu anda, hata ayıklama model CLR sürümlerinden önce tarafından desteklenmiyor [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Çıktı parametresi hala olarak bu hatadan sonra doğru değerine ayarlanır.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Bu hata ayıklayıcı desteği iddia sürümünden büyük CLR sürümüdür. `pwszVersion` Çıktı parametresi hala olarak bu hatadan sonra doğru değerine ayarlanır.|  
|E_NO_INTERFACE|`riidProcess` Arabirimi kullanılabilir değil.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Yapısı için tanınan bir değer yok `wStructVersion`. Şu anda yalnızca kabul edilen değeri 0'dır.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: 1598130eb097655d3e83689956eb3614103eb573
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860370"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess Yöntemi
İşlemde yüklü olan bir ortak dil çalışma zamanı (CLR) modülüne karşılık gelen ICorDebugProcess arabirimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Hedef işlemdeki bir modülün temel adresi. COR_E_NOT_CLR, belirtilen modül bir CLR modülü değilse döndürülecek.  
  
 `pDataTarget`  
 'ndaki Yönetilen hata ayıklayıcı işlem durumunu incelemeye izin veren bir veri hedefi soyutlama. Hata ayıklayıcının [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini uygulaması gerekir. Hata ayıklanan CLR 'nin bilgisayara yerel olarak yüklenmediği senaryoları desteklemek için [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimini uygulamalısınız.  
  
 `pLibraryProvider`  
 'ndaki Sürüme özgü hata ayıklama kitaplıklarının isteğe bağlı olarak konumlandırılma ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi. Bu parametre yalnızca `ppProcess` veya `pFlags` değilse gereklidir. `null`  
  
 `pMaxDebuggerSupportedVersion`  
 'ndaki Bu hata ayıklayıcının hata ayıklayabilecekleri en yüksek CLR sürümü. Bu hata ayıklayıcının desteklediği en son CLR sürümünden birincil, ikincil ve derleme sürümlerini belirtmeniz ve Düzeltme numarasını gelecekteki yerinde CLR bakım yayınlarına uyum sağlayacak şekilde 65535 olarak ayarlamanız gerekir.  
  
 `riidProcess`  
 'ndaki Alınacak ICorDebugProcess arabiriminin KIMLIĞI. Şu anda kabul edilen değerler IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 dışı Tarafından `riidProcess`tanımlanan com arabirimine yönelik bir işaretçi.  
  
 `pVersion`  
 [in, out] CLR sürümü. Girişte bu değer olabilir `null`. Ayrıca, bir [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) yapısına işaret edebilir, bu durumda yapının `wStructVersion` alanı 0 (sıfır) olarak başlatılmalıdır.  
  
 Çıkışta, döndürülen `CLR_DEBUGGING_VERSION` yapı CLR için sürüm bilgileriyle doldurulur.  
  
 `pdwFlags`  
 dışı Belirtilen çalışma zamanına ilişkin bilgilendirme bayrakları. Bayrakların açıklaması için [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) konusuna bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pDataTarget``null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) geri çağırması bir hata döndürüyor veya geçerli bir tanıtıcı sağlamıyor.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget`çalışma zamanının bu sürümü için gerekli veri hedefi arabirimlerini uygulamaz.|  
|CORDBG_E_NOT_CLR|Belirtilen modül bir CLR modülü değil. Bu HRESULT, bellek bozulduğundan bir CLR modülü algılanmadığında da döndürülür, modül kullanılabilir değildir veya CLR sürümü dolgu sürümünden daha geç.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Bu çalışma zamanı sürümü bu hata ayıklama modelini desteklemiyor. Şu anda, hata ayıklama modeli .NET Framework 4 ' den önceki CLR sürümleri tarafından desteklenmez. `pwszVersion` Output parametresi hala bu hatadan sonra doğru değere ayarlanmış.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|CLR sürümü, bu hata ayıklayıcı tarafından desteklenen sürümden daha büyük. `pwszVersion` Output parametresi hala bu hatadan sonra doğru değere ayarlanmış.|  
|E_NO_INTERFACE|`riidProcess` Arabirim kullanılamıyor.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Yapının için `wStructVersion`tanınan bir değeri yok. Bu zaman kabul edilen tek değer 0 ' dır.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: b270a6691d4e4ee4a5d0b42f424694eb7993e4e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504153"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi
Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` [ \<startup> öğe](../../configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde özniteliği kullanarak, eski etkinleştirme API 'Lerinin doğrudan kullanımını veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki Gerekli. Şu anda bu parametre için geçerli olan tek değer `IID_ICLRRuntimeInfo` .  
  
 `ppUnk`  
 dışı Gerekli. Bu yöntem döndüğünde, eski etkinleştirme ilkesine bağlanan bir çalışma zamanını temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı ve eski etkinleştirme ilkesine bağlanan bir çalışma zamanı döndürdü.|  
|S_FALSE|Yöntem başarıyla tamamlandı, ancak eski bir çalışma zamanı henüz bağlanmadı.|  
|E_NOINTERFACE|Yöntem, eski etkinleştirme ilkesine bağlanan, ancak `riid` Bu çalışma zamanı tarafından desteklenmeyen bir çalışma zamanı buldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Hosting](index.md)

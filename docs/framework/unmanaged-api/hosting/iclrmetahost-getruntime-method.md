---
title: ICLRMetaHost::GetRuntime Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b71d0f29d770b2722b0dfaabc8b9667e524c99e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207610"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime Metodu
Alır [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ortak dil çalışma zamanı (CLR) belirli bir sürümüne karşılık gelen arabirimi. Bu yöntem yerine geçer [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ile kullanılan işlev [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzVersion`  
 [in] .NET Framework derleme sürümü biçiminde meta verilerde depolanan "v*A*. *B*[. *X*] ". *A*, *B*, ve *X* ana sürüm, ikincil sürüm ve derleme numarasını karşılık gelen ondalık sayılardır.  
  
> [!NOTE]
>  C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64 altında göründüğü gibi bu parametre .NET Framework sürümü için dizin adı eşleşmelidir.  
  
 Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *X*"burada *X* yüklü derleme sayısına bağlıdır. "V" ön eki gereklidir.  
  
 `riid`  
 [in] İstendiği arayüz tanımlayıcısı. Şu anda, bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo ' dir.  
  
 `ppRuntime`  
 [out] Bir işaretçi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) istenen çalışma zamanı için karşılık gelen arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzVersion` veya `ppRuntime` null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile eski arabirimleri gibi tutarlı bir şekilde etkileşim [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi ve eski işlevler kullanım dışı gibi `CorBindTo*` işlevleri (bkz [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API'sini barındıran .NET Framework 2.0). Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API için görünür olan ve yeni API ile yüklenen çalışma zamanları eski API'sine görülebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

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
ms.openlocfilehash: f4b796942df153bf2c6ab703d748449331c9a0b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939855"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime Metodu
Ortak dil çalışma zamanının (CLR) belirli bir sürümüne karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimini alır. Bu yöntem, [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzVersion`  
 'ndaki Meta verilerde depolanan .NET Framework derleme sürümü, "v*A*" biçimindedir. *B* [. *X*] ". *A*, *B*ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.  
  
> [!NOTE]
> Bu parametre C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşmelidir.  
  
 Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır. "V" ön eki gereklidir.  
  
 `riid`  
 'ndaki İstenen arabirim için tanımlayıcı. Şu anda bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo ' dir.  
  
 `ppRuntime`  
 dışı İstenen çalışma zamanına karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzVersion`ya `ppRuntime` da null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi gibi eski arabirimlere ve kullanım dışı bırakılan `CorBindTo*` işlevler gibi eski işlevlere sürekli olarak etkileşime girer (bkz. .NET Framework 2,0 barındırma içindeki [kullanım dışı clr barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) APı). Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API 'ye görünür ve yeni API ile yüklenen çalışma zamanları eski API 'ye görünür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MetaHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

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
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504202"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime Metodu
Ortak dil çalışma zamanının (CLR) belirli bir sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini alır. Bu yöntem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) bayrağıyla kullanılan [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzVersion`  
 'ndaki Meta verilerde depolanan .NET Framework derleme sürümü, "v*A*" biçimindedir. *B*[.* X*] ". *A*, *B*ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.  
  
> [!NOTE]
> Bu parametre C:\Windows\Microsoft.NET\Framework veya C:\Windows\Microsoft.NET\Framework64. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşmelidir.  
  
 Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır. "V" ön eki gereklidir.  
  
 `riid`  
 'ndaki İstenen arabirim için tanımlayıcı. Şu anda bu parametre için geçerli olan tek değer IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 dışı İstenen çalışma zamanına karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzVersion`ya da `ppRuntime` null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi gibi eski arabirimlere ve kullanım dışı bırakılan işlevler gibi eski işlevlere sürekli olarak etkileşime girer `CorBindTo*` (bkz. .NET Framework 2,0 barındırma API 'SINDEKI [kullanım dışı clr barındırma işlevleri](deprecated-clr-hosting-functions.md) ). Diğer bir deyişle, eski API ile yüklenen çalışma zamanları yeni API 'ye görünür ve yeni API ile yüklenen çalışma zamanları eski API 'ye görünür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
- [Hosting](index.md)

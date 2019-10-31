---
title: ICLRRuntimeInfo::IsLoaded Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: e0ab16348abbaff00152f2b259ccafdd331174df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136355"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded Yöntemi
[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma ZAMANıNıN (CLR) bir işleme yüklenip yüklenmediğini gösterir. Çalışma zamanı, aynı zamanda başlatılmadan de yüklenebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hndProcess`  
 'ndaki İşlem için bir tanıtıcı.  
  
 `pbLoaded`  
 [out] CLR işleme yüklenirse `true`; Aksi takdirde, `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pbLoaded` null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, aşağıdaki işlevler ve arabirimler ile geriye dönük olarak uyumludur:  
  
- [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API 'si).  
  
- [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi (.NET Framework 2,0 barındırma API 'si).  
  
- Kullanım dışı `CorBindTo*` işlevleri (bkz. .NET Framework 2,0 barındırma API 'sindeki [kullanım DıŞı clr barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) ).  
  
 Bir konak, CLR 'nin belirli bir sürümünü oluşturmak için [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) işlevi gibi kullanım dışı `CorBindTo*` işlevlerinden birini çağırabilir. Konak daha sonra [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metodunu çağırabilir ve bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi elde etmek için aynı sürüm numarasını belirtebilir.  
  
 Daha sonra ana bilgisayar döndürülen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimindeki `IsLoaded` yöntemini çağırırsa `pbLoaded` `true`döndürür; Aksi takdirde, `false`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

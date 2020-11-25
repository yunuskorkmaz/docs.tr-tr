---
title: ICLRRuntimeInfo::GetDefaultStartupFlags Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 2f828a3720f7313ee9cb851c6adae78bd5ea4fe8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732104"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags Metodu

Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwStartupFlags`  
 dışı Şu anda ayarlanmış olan ana bilgisayar başlatma bayraklarının işaretçisi.  
  
 `pwzHostConfigFile`  
 dışı Geçerli ana bilgisayar yapılandırma dosyasının dizin yoluna yönelik bir işaretçi.  
  
 `pcchHostConfigFile`  
 [in, out] Girişte, `pwzHostConfigFile` arabellek taşmalarını önlemek için, boyutu. `pwzHostConfigFile`Null ise, yöntemi `pwzHostConfigFile` ön ayırma için gereken boyutunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, varsayılan bayrak değerlerini ( `STARTUP_CONCURRENT_GC` ve `NULL` ) ya da [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md) `CorBind*` Bu çalışma zamanına bağlılarsa yöntemlerin herhangi biri tarafından ayarlanan değerleri döndürür (ve) veya bir önceki çağrı tarafından belirtilen değerleri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)

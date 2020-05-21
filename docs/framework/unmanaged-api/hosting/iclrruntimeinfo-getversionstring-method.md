---
title: ICLRRuntimeInfo::GetVersionString Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: ccf48b6aea25bd602b55727c2e5958811702f6bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762584"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString Yöntemi
Belirli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.  
  
 Bu yöntem aşağıdaki işlevlerin yerini alır:  
  
- [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzBuffer`  
 dışı "V*A*" biçimindeki derleme sürümü .NET Framework. *B*[.* X*] ". *A*, *B*ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır. *X* isteğe bağlıdır. *X* yoksa, izleyen bir dönem yoktur.  
  
> [!NOTE]
> Bu parametrenin .NET Framework sürümünün dizin adıyla eşleşmesi gerekir, çünkü C:\Windows\Microsoft.NET\Framework. altında görünür.  
  
 Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *x*", burada *x* , yüklü yapı numarasına bağlıdır. "V" ön ekinin zorunlu olduğunu unutmayın.  
  
 `pchBuffer`  
 [in, out] `pwzBuffer`Arabellek taşmalarını önlemek için boyutunu belirtir. İse `pwzBuffer` `null` , `pchBuffer` `pwzBuffer` ön ayırmaya izin vermek için gereken boyutunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzBuffer`ya da `pchBuffer` null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma](index.md)

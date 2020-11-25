---
title: ICLRRuntimeInfo::GetRuntimeDirectory Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 24679118e4255282f7da3ff8be2ce9c08250e181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732053"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory Metodu

Bu arabirimle ilişkili ortak dil çalışma zamanının (CLR) yükleme dizinini alır.  
  
 Bu yöntem 2,0, 3,0 ve 3,5 .NET Framework sürümlerinde sunulan [GetCORSystemDirectory](getcorsystemdirectory-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzBuffer`  
 dışı CLR yükleme dizinini döndürür. Yükleme yolu tam olarak nitelenir; Örneğin, "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".  
  
 `pchBuffer`  
 [in, out] `pwzBuffer` Arabellek taşmalarını önlemek için boyutunu belirtir. `pwzBuffer`Null ise, `pchBuffer` gereken boyutunu döndürür `pwzBuffer` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzBuffer` ya da `pchBuffer` null.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Hosting](index.md)

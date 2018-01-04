---
title: "ICLRRuntimeInfo::LoadLibrary Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadLibrary
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b688a4f2557c5ab2ef112e13b411e25ad47b8c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a>ICLRRuntimeInfo::LoadLibrary Yöntemi
.NET Framework kitaplığı tarafından temsil edilen ortak dil çalışma zamanı (CLR) yükler bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.  
  
 Bu yöntem yerini [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzDllName`  
 [in] Yüklenecek derlemenin adı.  
  
 `phndModule`  
 [out] Yüklenen derleme için bir tanıtıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzDllName`veya `phndModule` null.|  
|E_OUTOFMEMORY|İsteği işlemek yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca .NET Framework yeniden dağıtılabilir paketinde DLL'lerini yükler. Kullanıcı tarafından oluşturulan derlemeler yüklenemiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

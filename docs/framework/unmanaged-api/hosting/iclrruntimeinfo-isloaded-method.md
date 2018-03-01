---
title: "ICLRRuntimeInfo::IsLoaded Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f1a83db3a5fc7b5f8b4ad763208fa31ab8f840e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded Yöntemi
Ortak dil çalışma zamanı (CLR) ile ilişkili olup olmadığını gösteren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi süreç içine yüklenir. Bir çalışma zamanı da başlatılmadan yüklenebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hndProcess`  
 [in] İşlem için bir tanıtıcı.  
  
 `pbLoaded`  
 [out] `true` CLR işlemine yüklenen; Aksi takdirde ise `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pbLoaded`null şeklindedir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geriye dönük olarak uyumlu bu yöntem aşağıdaki işlevler ve arabirimleri ile:  
  
-   [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi (.NET Framework sürüm 1 barındırma API).  
  
-   [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi (API barındırma .NET Framework 2.0).  
  
-   Kullanım dışı `CorBindTo*` işlevleri (bkz [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API barındırma .NET Framework 2.0).  
  
 Bir ana bilgisayar kullanım dışı birini çağırabilir `CorBindTo*` gibi işlevleri [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) CLR belirli bir sürümünü oluşturmak için işlevi. Ana bilgisayar ardından çağırabilirsiniz [Iclrmetahost::getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) yöntemi ve almak için aynı sürüm numarası belirtin bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.  
  
 Konak sonra çağırırsa `IsLoaded` yöntemi döndürülen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi, `pbLoaded` döndürür `true`; Aksi takdirde döndürdüğü `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

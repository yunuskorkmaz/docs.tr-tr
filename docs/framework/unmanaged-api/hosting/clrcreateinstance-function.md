---
title: CLRCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571e2698b980b12b89a5b689efb868a34a3ef71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167667"
---
# <a name="clrcreateinstance-function"></a>CLRCreateInstance İşlevi
Üç arabirimlerinden birini sağlar: [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), veya [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `clsid`  
 [in] Üç sınıf tanımlayıcıları biri: Clsıd_clrmetahost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.  
  
 `riid`  
 [in] Üç arabirim tanımlayıcıları (IID'leri) biri: Iıd_ıclrmetahost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.  
  
 `ppInterface`  
 [out] Üç arabirimlerinden birini: [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), veya [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`ppInterface` NULL olur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablo için desteklenen kombinasyonlar gösterir `clsid` ve `riid`.  
  
|`clsid`|`riid`|  
|--------------|------------|  
|CLSID_CLRMetaHost|IID_ICLRMetaHost|  
|CLSID_CLRMetaHostPolicy|IID_ICLRMetaHostPolicy|  
|CLSID_CLRDebugging|IID_ICLRDebugging|  
  
 Aşağıdaki kod nasıl kullanılacağını gösterir `CLRCreateInstance` üç arabirimlerinin almak için:  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

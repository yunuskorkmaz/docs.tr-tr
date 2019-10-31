---
title: IGCHost::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 1ae50fb3ff15097f9a6ca5839f3832bcfc58d3f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134849"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits Yöntemi
Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.  
  
> [!IMPORTANT]
> 4,5 .NET Framework başlayarak, [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` daha büyük değerlere ayarlayabilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `SegmentSize`  
 'ndaki Çöp toplama sistemi tarafından kullanılan segmentin boyutu.  
  
 `MaxGen0Size`  
 'ndaki 0 üretimi için en büyük boyut.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetGCStartupLimits` yöntemi yalnızca bir kez çağrılabilir. Bu değerler daha sonra değiştirilemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

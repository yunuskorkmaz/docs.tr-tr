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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87ba947b9564f82f8daf8cd2ba0acac5cc3587ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928672"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits Yöntemi
Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.  
  
> [!IMPORTANT]
> 4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük `DWORD` değerlere ayarlayabilirsiniz.  
  
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
 `SetGCStartupLimits` Yöntemi yalnızca bir kez çağrılabilir. Bu değerler daha sonra değiştirilemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** GCHost. IDL, GCHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

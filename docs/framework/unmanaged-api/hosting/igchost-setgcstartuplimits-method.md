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
ms.openlocfilehash: 365261883f0b81884bb7cf70614628c05f9067c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993271"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits Yöntemi
Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kesim boyutu ayarlayabileceğiniz ve en fazla nesil 0 boyutu daha büyük değerler `DWORD` kullanarak [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `SegmentSize`  
 [in] Çöp toplama sistem tarafından kullanılan kesim boyutu.  
  
 `MaxGen0Size`  
 [in] Nesil 0 en büyük boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetGCStartupLimits` Yöntemi çağrılabilir yalnızca bir kez. Bu değerler daha sonra değiştirilemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

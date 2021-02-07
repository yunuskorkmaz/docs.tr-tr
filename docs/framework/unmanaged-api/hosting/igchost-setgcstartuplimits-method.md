---
description: 'Daha fazla bilgi edinin: IGCHost:: SetGCStartupLimits yöntemi'
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
ms.openlocfilehash: 91c74d54189bbfb7e9f208e507fe6e75b7023e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709509"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits Yöntemi

Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.  
  
> [!IMPORTANT]
> 4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük değerlere ayarlayabilirsiniz.  
  
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

 `SetGCStartupLimits`Yöntemi yalnızca bir kez çağrılabilir. Bu değerler daha sonra değiştirilemez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](igchost-interface.md)

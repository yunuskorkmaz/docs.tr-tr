---
title: EPolicyAction Numaralandırması
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138227"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction Numaralandırması
[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) tarafından tanımlanan Işlemler ve [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)tarafından tanımlanan hatalar için konağın ayarlayaşabilemeyen ilke eylemlerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eAbortThread`|Ortak dil çalışma zamanının (CLR) iş parçacığını düzgün bir şekilde iptal etmesi gerektiğini belirtir. Düzgün bir şekilde iptali, tüm `finally` blokları, iş parçacığı iptalleriyle ilgili tüm `catch` blokları ve sonlandırıcıları çalıştırma girişimlerini içerir.|  
|`eDisableRuntime`|CLR 'nin devre dışı bir durum girmesi gerektiğini belirtir. Etkilenen işlemde başka yönetilen kod yürütülemez ve iş parçacıklarının CLR 'ye girmaları engellenir.|  
|`eExitProcess`|CLR 'nin, sonlandırıcıları çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme dahil olmak üzere işlemden düzgün bir şekilde çıkış denemesi gerektiğini belirtir.|  
|`eFastExitProcess`|CLR 'nin sonlandırıcıları çalıştırmadan veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirmeksizin işlemden hemen çıkış gerektiğini belirtir. Ancak, bildirim hata ayıklayıcıya gönderilir.|  
|`eNoAction`|Hiçbir eylemin alıngerekmediğini belirtir.|  
|`eRudeAbortThread`|CLR 'nin bir işlenmemiş iş parçacığı iptali gerçekleştirmesi gerektiğini belirtir. Yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> işaretlenen `catch` ve `finally` blokları yürütülür.|  
|`eRudeExitProcess`|CLR 'nin sonlandırıcılar veya günlüğe kaydetme işlemlerini çalıştırmadan işlemden çıkması gerektiğini belirtir.|  
|`eRudeUnloadAppDomain`|CLR 'nin <xref:System.AppDomain>bir işlenmemiş yüklemesini gerçekleştirmesi gerektiğini belirtir. Yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> ile işaretlenen sonlandırıcılar yürütülür. Benzer şekilde, yığındaki bu <xref:System.AppDomain> sahip tüm iş parçacıkları bir `ThreadAbortException`alır, ancak yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> ile işaretlenen `catch` ve `finally` blokları yürütülür.|  
|`eThrowException`|Koşula uygun bir özel durum (örneğin, bellek dışı, arabellek taşması vb.) oluşturulması gerektiğini belirtir.|  
|`eUnloadAppDomain`|<xref:System.AppDomain> yüklemesi gerektiğini belirtir. CLR sonlandırıcıları çalıştırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabiriminin yöntemlerini çağırarak ilke eylemlerini ayarlar. İşlenmemiş ve düzgün kaldırma hakkında bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

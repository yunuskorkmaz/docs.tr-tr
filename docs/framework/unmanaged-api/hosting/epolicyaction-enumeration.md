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
ms.openlocfilehash: 8788d6e2220778a3f0926d5ed3dd59142487bcca
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616196"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction Numaralandırması
[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) tarafından tanımlanan Işlemler ve [EClrFailure](eclrfailure-enumeration.md)tarafından tanımlanan hatalar için konağın ayarlayaşabilemeyen ilke eylemlerini açıklar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`eAbortThread`|Ortak dil çalışma zamanının (CLR) iş parçacığını düzgün bir şekilde iptal etmesi gerektiğini belirtir. Düzgün bir şekilde iptali, tüm blokları çalıştırma girişimlerini `finally` , `catch` iş parçacığı iptalleriyle ilgili tüm blokları ve sonlandırıcıları içerir.|  
|`eDisableRuntime`|CLR 'nin devre dışı bir durum girmesi gerektiğini belirtir. Etkilenen işlemde başka yönetilen kod yürütülemez ve iş parçacıklarının CLR 'ye girmaları engellenir.|  
|`eExitProcess`|CLR 'nin, sonlandırıcıları çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme dahil olmak üzere işlemden düzgün bir şekilde çıkış denemesi gerektiğini belirtir.|  
|`eFastExitProcess`|CLR 'nin sonlandırıcıları çalıştırmadan veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirmeksizin işlemden hemen çıkış gerektiğini belirtir. Ancak, bildirim hata ayıklayıcıya gönderilir.|  
|`eNoAction`|Hiçbir eylemin alıngerekmediğini belirtir.|  
|`eRudeAbortThread`|CLR 'nin bir işlenmemiş iş parçacığı iptali gerçekleştirmesi gerektiğini belirtir. Yalnızca `catch` `finally` ile işaretli olan ve blokları <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eRudeExitProcess`|CLR 'nin sonlandırıcılar veya günlüğe kaydetme işlemlerini çalıştırmadan işlemden çıkması gerektiğini belirtir.|  
|`eRudeUnloadAppDomain`|CLR 'nin bir işlenmemiş yüklemesini gerçekleştirmesi gerektiğini belirtir <xref:System.AppDomain> . Yalnızca ile işaretlenen sonlandırıcılar <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür. Benzer şekilde, yığınında buna sahip olan tüm iş parçacıkları <xref:System.AppDomain> bir alır `ThreadAbortException` , ancak yalnızca `catch` `finally` ile işaretlenmiş olan ve blokları <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eThrowException`|Koşula uygun bir özel durum (örneğin, bellek dışı, arabellek taşması vb.) oluşturulması gerektiğini belirtir.|  
|`eUnloadAppDomain`|' Nin <xref:System.AppDomain> yüklemesi gerektiğini belirtir. CLR sonlandırıcıları çalıştırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabiriminin yöntemlerini çağırarak ilke eylemlerini ayarlar. İşlenmemiş ve düzgün kaldırma hakkında bilgi için bkz. [EClrOperation](eclroperation-enumeration.md) numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](eclrfailure-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80a0e8d37e834ea0a7623517e2e1228a79d9ea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655718"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction Numaralandırması
Ana bilgisayar tarafından açıklanan işlemleri için ayarlayabileceğiniz İlkesi eylemleri açıklar [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ve hataları tarafından açıklanan [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`eAbortThread`|Ortak dil çalışma zamanı (CLR) iş parçacığı düzgün bir şekilde iptal belirtir. Normal iptal tüm çalıştırma girişimlerini içerir `finally` engeller, tüm `catch` blokları, iş parçacığı iptalleri ve sonlandırıcılar ilgili.|  
|`eDisableRuntime`|CLR devre dışı durumuna girdiğini belirtir. Yönetilen kod etkilenen işlemde başka yürütülebilecek ve iş parçacıkları CLR girmesini engellenir.|  
|`eExitProcess`|CLR işleminin sonlandırıcılar çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme gibi normal bir çıkış denemesi belirtir.|  
|`eFastExitProcess`|CLR işlemi hemen sonlandırıcılar çalıştırma veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştiren çıkış belirtir. Nowever, hata ayıklayıcı için bildirim gönderilir.|  
|`eNoAction`|Hiçbir işlem yapılmadı olduğunu belirtir.|  
|`eRudeAbortThread`|CLR rude iş parçacığı iptal gerçekleştirileceğini belirtir. Yalnızca `catch` ve `finally` simgesiyle işaretli blok <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eRudeExitProcess`|Sonlandırıcılar çalıştıran veya işlem günlüğü CLR işleminden çıkış olduğunu belirtir.|  
|`eRudeUnloadAppDomain`|CLR bir rude kaldırmaya gerçekleştirileceğini belirtir <xref:System.AppDomain>. Yalnızca bir sonlandırıcı işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür. Benzer şekilde, tüm iş parçacıkları bu <xref:System.AppDomain> almak, yığındaki bir `ThreadAbortException`, ancak yalnızca `catch` ve `finally` simgesiyle işaretli blok <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eThrowException`|Bellek yetersiz arabellek taşması ve benzeri, gibi koşula uygun bir özel durumun oluşturulmasını da belirtir.|  
|`eUnloadAppDomain`|Belirten <xref:System.AppDomain> kaldırılmış olması gerekir. CLR, sonlandırıcılar çalıştırmayı dener.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar ilkesi eylemleri yöntemleri çağırarak ayarlar [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimi. İşlenmemiş ve normal iptal edilmesini hakkında daha fazla bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) sabit listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

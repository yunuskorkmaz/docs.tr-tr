---
title: "EPolicyAction Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f2c3a4138adfa354de07bc6df4e51d7697598b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction Numaralandırması
Ana bilgisayar tarafından açıklanan işlemleri için ayarlayabileceğiniz ilke eylemleri açıklar [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ve hataları tarafından açıklanan [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
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
|`eAbortThread`|Ortak dil çalışma zamanı (CLR) iş parçacığı düzgün biçimde iptal belirtir. Tüm çalıştırma denemelerini normal iptal içeren `finally` engeller, herhangi bir `catch` blokları ilgili iş parçacığı iptalleri ve sonlandırıcılar.|  
|`eDisableRuntime`|CLR devre dışı durumuna girmelisiniz belirtir. Yönetilen kod etkilenen işleminde başka çalıştırılabilir ve iş parçacıkları CLR girmesini engellenir.|  
|`eExitProcess`|CLR işleminin sonlandırıcılar çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme gibi normal bir çıkış denemesi belirtir.|  
|`eFastExitProcess`|CLR işlemi hemen sonlandırıcılar çalıştıran veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme çıkış belirtir. Nowever, hata ayıklayıcı için bildirim gönderilir.|  
|`eNoAction`|Hiçbir işlem yapılmadı olduğunu belirtir.|  
|`eRudeAbortThread`|CLR utangaç iş parçacığı iptal gerçekleştirileceğini belirtir. Yalnızca `catch` ve `finally` blokları işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eRudeExitProcess`|CLR sonlandırıcılar çalıştıran veya işlem günlüğü işlemi kapanmamalıdır belirtir.|  
|`eRudeUnloadAppDomain`|CLR, utangaç unload gerçekleştirileceğini belirtir <xref:System.AppDomain>. Yalnızca sonlandırıcılar işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür. Benzer şekilde, tüm iş parçacıklarını bu <xref:System.AppDomain> kendi yığınında alma bir `ThreadAbortException`, ancak yalnızca `catch` ve `finally` blokları işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.|  
|`eThrowException`|Bellek yetersiz arabellek taşması ve benzeri, gibi koşula uygun bir özel durum olduğunu belirtir.|  
|`eUnloadAppDomain`|Belirleyen <xref:System.AppDomain> kaldırılmış olması gerekir. CLR sonlandırıcılar çalıştırmayı dener.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar ilkesi eylemleri yöntemlerini çağırarak ayarlar [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimi. Utangaç ve normal iptalleri hakkında daha fazla bilgi için bkz: [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [EClrFailure numaralandırması](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [Iclrpolicymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Ihostpolicymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Barındırma numaralandırmaları](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

---
title: "EClrOperation Numaralandırması"
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
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a>EClrOperation Numaralandırması
Bir ana bilgisayar ilkesi eylemleri uygulayabilirsiniz işlemlerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|Ana bilgisayar ilkesi olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz bir <xref:System.AppDomain> (utangaç) normal olmayan bir şekilde kaldırıldı.|  
|`OPR_AppDomainUnload`|Ana bilgisayar ilkesi olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz bir <xref:System.AppDomain> kaldırılır.|  
|`OPR_FinalizerRun`|Ana bilgisayar ilkesi sonlandırıcılar çalıştırdığınızda, gerçekleştirilecek eylemleri belirtebilirsiniz.|  
|`OPR_ProcessExit`|Ana bilgisayar ilkesi işlem çıktığında gerçekleştirilecek eylemleri belirtebilirsiniz.|  
|`OPR_ThreadAbort`|Ana bilgisayar ilkesi bir iş parçacığı iptal edildiğinde gerçekleştirilecek eylemleri belirtebilirsiniz.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Ana bilgisayar ilkesi utangaç iş parçacığı iptal kod kritik bir bölgede olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Ana bilgisayar olması utangaç iş parçacığı iptal kod kritik olmayan bir bölgede oluştuğunda İlkesi eylemler belirtebilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısının iptal eder ve kaynak arasında kodu ve kod kritik olmayan bölgelerde ortaya kritik bölgelerdeki oluşan ayırma hatalarını ayırır. Bu ayrım kodda bir hata oluştuğu bağlı olarak farklı ilkeleri ayarlamak ana izin verecek şekilde tasarlanmıştır.  
  
 A *kritik bölge kodu* burada CLR garanti etmez, bir görevi iptal etme veya kaynakları yalnızca geçerli görev etkiler için bir isteği tamamlamak başarısız olan herhangi bir alandır. Bir görev bir kilit ve bellek ayırma isteği yaptıktan sonra hata olduğunu gösteren bir HRESULT alır, örneğin, bunu yalnızca kararlılığını emin olmak için bu görev iptal etmek yeterli değil <xref:System.AppDomain>, çünkü <xref:System.AppDomain> diğer içerebilir aynı kilidi için bekleyen görevler. Geçerli bırakmasını görev olanlar yanıt vermemesine (veya askıda) diğer görevlerin neden olabilecek süresiz olarak. Böyle bir durumda, konak tüm kaldırma yeteneği gereken <xref:System.AppDomain> risk olası kararsızlığı yerine.  
  
 A *kritik olmayan bölge kodu*, diğer yandan, burada CLR ise bir durdurma veya bir hata yalnızca hata oluştuğu görev etkiler bir bölgedir.  
  
 CLR de normal ve normal olmayan (utangaç) iptalleri arasında ayırır. Genel olarak, normal veya normal iptal utangaç durdurma gibi garanti yaparken bir görevi iptal etmeden önce özel durum işleme rutinleri ve sonlandırıcılar çalıştırmak için her türlü çabayı göstermektedir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

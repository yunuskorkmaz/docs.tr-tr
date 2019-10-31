---
title: EClrOperation Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131155"
---
# <a name="eclroperation-enumeration"></a>EClrOperation Numaralandırması
Bir konağın ilke eylemlerini uygulayabileceği işlemler kümesini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`OPR_AppDomainRudeUnload`|Ana bilgisayar, bir <xref:System.AppDomain>, düzgün olmayan (Rude) bir biçimde kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_AppDomainUnload`|Ana bilgisayar, bir <xref:System.AppDomain> kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_FinalizerRun`|Konak, sonlandırıcılar çalıştırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ProcessExit`|Ana bilgisayar, işlem çıktığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadAbort`|Konak, bir iş parçacığı iptal edildiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Ana bilgisayar, kritik kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Ana bilgisayar kritik olmayan bir kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısı, kod ve kritik olmayan kod bölgelerinde oluşan önemli bölgelerde oluşan iptal ve kaynak ayırma arızalarını birbirinden ayırır. Bu ayrım, ana bilgisayarların kodda bir hatanın oluştuğu yere bağlı olarak farklı ilkeler değiştirmesine izin vermek için tasarlanmıştır.  
  
 *Kritik kod bölgesi* , clr 'nin bir görevi iptal etme veya kaynakların bir isteği tamamlayamamakta olduğunu garanti edemediği, yalnızca geçerli görevi etkilediği bir alandır. Örneğin, bir görev bir kilit tutuyor ve bir bellek ayırma isteği yapıldığında hata belirten bir HRESULT alırsa, <xref:System.AppDomain> başka görevler içerebileceğinden <xref:System.AppDomain>kararlılığını sağlamak için bu görevi durdurmak yeterli değildir aynı kilit bekleniyor. Geçerli görevi bırakmak için diğer görevlerin yanıt vermemesine neden olabilir. Böyle bir durumda, konağın potansiyel kararsızlığı yerine tüm <xref:System.AppDomain> kaldırabilmesini gerektirir.  
  
 Diğer taraftan, *kritik olmayan bir kod bölgesi*, clr 'nin bir iptal ya da bir başarısızlığın yalnızca hatanın gerçekleştiği görevi etkileyeceğini garanti edebildiği bir bölgedir.  
  
 CLR, düzgün kapanma ve düzgün olmayan (Rude) kaldırma işlemini de ayırt eder. Genel olarak, normal veya düzgün bir şekilde iptali, bir görevi iptal etmeden önce özel durum işleme yordamlarını ve sonlandırıcıları çalıştırma çabalarının yanı sıra bir işlenmemiş iptali bu tür garantiyi yapmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

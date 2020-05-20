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
ms.openlocfilehash: e7cb1c2070e760258e548d2f45e3b6ed11e046c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616327"
---
# <a name="eclroperation-enumeration"></a>EClrOperation Numaralandırması
Bir konağın ilke eylemlerini uygulayabileceği işlemler kümesini açıklar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`OPR_AppDomainRudeUnload`|Ana bilgisayar, <xref:System.AppDomain> normal olmayan (Rude) bir biçimde kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_AppDomainUnload`|Ana bilgisayar, kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir <xref:System.AppDomain> .|  
|`OPR_FinalizerRun`|Konak, sonlandırıcılar çalıştırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ProcessExit`|Ana bilgisayar, işlem çıktığında gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadAbort`|Konak, bir iş parçacığı iptal edildiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Ana bilgisayar, kritik kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Ana bilgisayar kritik olmayan bir kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısı, kod ve kritik olmayan kod bölgelerinde oluşan önemli bölgelerde oluşan iptal ve kaynak ayırma arızalarını birbirinden ayırır. Bu ayrım, ana bilgisayarların kodda bir hatanın oluştuğu yere bağlı olarak farklı ilkeler değiştirmesine izin vermek için tasarlanmıştır.  
  
 *Kritik kod bölgesi* , clr 'nin bir görevi iptal etme veya kaynakların bir isteği tamamlayamamakta olduğunu garanti edemediği, yalnızca geçerli görevi etkilediği bir alandır. Örneğin, bir görev bir kilit tutuyor ve bir bellek ayırma isteği yapıldığında hata belirten bir HRESULT alırsa, ' nin kararlılığını sağlamak için bu görevi durdurmak yeterli değildir <xref:System.AppDomain> çünkü, <xref:System.AppDomain> aynı kilidi bekleyen diğer görevleri içerebilir. Geçerli görevi bırakmak için diğer görevlerin yanıt vermemesine neden olabilir. Böyle bir durumda, konağın <xref:System.AppDomain> risk olası dengesizinden değil, tümünü kaldırma yeteneği olması gerekir.  
  
 Diğer taraftan, *kritik olmayan bir kod bölgesi*, clr 'nin bir iptal ya da bir başarısızlığın yalnızca hatanın gerçekleştiği görevi etkileyeceğini garanti edebildiği bir bölgedir.  
  
 CLR, düzgün kapanma ve düzgün olmayan (Rude) kaldırma işlemini de ayırt eder. Genel olarak, normal veya düzgün bir şekilde iptali, bir görevi iptal etmeden önce özel durum işleme yordamlarını ve sonlandırıcıları çalıştırma çabalarının yanı sıra bir işlenmemiş iptali bu tür garantiyi yapmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](eclrfailure-enumeration.md)
- [EPolicyAction Sabit Listesi](epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](ihostpolicymanager-interface.md)
- [Barındırma Sabit Listeleri](hosting-enumerations.md)

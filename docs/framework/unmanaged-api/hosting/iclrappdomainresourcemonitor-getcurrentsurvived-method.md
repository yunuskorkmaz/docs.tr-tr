---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: a73c0731c79dea3a0c411fe27a864ec9ac4e20b2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616027"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu
Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwAppDomainId`  
 'ndaki İstenen uygulama etki alanının KIMLIĞI.  
  
 `pAppDomainBytesSurvived`  
 dışı Bu uygulama etki alanı tarafından tutulan son çöp toplamadan sonra kalan bayt sayısına yönelik bir işaretçi. Tam bir koleksiyon sonrasında bu sayı doğru ve tamamlanmıştır. Kısa ömürlü bir koleksiyon sonrasında bu sayı muhtemelen tamamlanmamış olur. Bu parametre olabilir `null` .  
  
 `pRuntimeBytesSurvived`  
 dışı Son çöp toplamadan kalan toplam bayt sayısı için bir işaretçi. Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki tutulan baytların sayısını temsil eder. Kısa ömürlü bir koleksiyon sonrasında bu sayı, kısa ömürlü neslerde canlı tutulan bayt sayısını temsil eder. Bu parametre olabilir `null` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|COR_E_APPDOMAINUNLOADED|Uygulama etki alanı kaldırıldı veya yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 İstatistikler, yalnızca tam ve çöp toplama işlemleri engellendikten sonra güncelleştirilir; diğer bir deyişle, koleksiyon gerçekleştiğinde uygulamayı durduran tüm nesilleri içeren bir koleksiyon. Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yüklemesi tam, engelleyici bir koleksiyon gerçekleştirir. Eşzamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.  
  
 `GetCurrentSurvived`Yöntemi, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAppDomainResourceMonitor Arabirimi](iclrappdomainresourcemonitor-interface.md)
- [Uygulama etki alanı kaynak Izleme](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Barındırma](index.md)

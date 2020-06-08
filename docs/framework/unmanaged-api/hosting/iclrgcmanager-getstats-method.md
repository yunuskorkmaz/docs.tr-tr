---
title: ICLRGCManager::GetStats Metodu
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504231"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats Metodu
Ortak dil çalışma zamanının çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStats`  
 [in, out] İstenen istatistikleri içeren bir [cor_gc_stats](cor-gc-stats-structure.md) örneği.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetStats`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, yalnızca alanı tarafından belirtilen istatistikleri hesaplar ve döndürür `Flags` `pStats` .  
  
 `Flags` [Cor_gc_stats](cor-gc-stats-structure.md) yapısındaki hangi istatistiklerin ayarlanacağını belirtmek için alanı [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırmanın bir veya daha fazla değerine ayarlayın.  
  
 Kullanım örneği aşağıdaki gibidir:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS Yapısı](cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES Sabit Listesi](cor-gc-stat-types-enumeration.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRGCManager Arabirimi](iclrgcmanager-interface.md)
- [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)

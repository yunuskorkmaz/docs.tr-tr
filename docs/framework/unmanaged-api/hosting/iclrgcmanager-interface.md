---
title: ICLRGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: dbe3df6bb20e5ad8f9eb534a366405eb9c33984f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678252"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager Arabirimi

Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.  
  
> [!NOTE]
> 4,5 .NET Framework başlayarak, [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD` [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınırdan daha büyük değerlere ayarlayabilirsiniz.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Collect Yöntemi](iclrgcmanager-collect-method.md)|Belirtilen oluşturma için bir çöp toplamayı zorlar.|  
|[GetStats Metodu](iclrgcmanager-getstats-method.md)|Çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.|  
|[SetGCStartupLimits Yöntemi](iclrgcmanager-setgcstartuplimits-method.md)|Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen türle uygular <xref:System.GC> . Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS Yapısı](cor-gc-stats-structure.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)

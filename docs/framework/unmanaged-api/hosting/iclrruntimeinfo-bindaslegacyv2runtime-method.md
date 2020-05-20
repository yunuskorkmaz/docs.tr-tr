---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703896"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi
Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilkesi kararlarının geçerli çalışma zamanını bağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli HRESULTs 'leri döndürür:  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi çalışma zamanı olarak zaten bağlandı.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli çalışma zamanı tüm eski CLR sürüm 2 etkinleştirme ilkesi kararlarında zaten bağlıysa (örneğin, `useLegacyV2RuntimeActivationPolicy` yapılandırma dosyasındaki [ \< Başlangıç> öğesindeki](../../configure-apps/file-schema/startup/startup-element.md) özniteliğini kullanarak), bu yöntem bir hata sonucu döndürmez; bunun yerine, yöntemin eski etkinleştirme ilkesini başarıyla bağlamış olması gibi, sonuç S_OK olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Barındırma](index.md)
- [\<başlangıç> öğesi](../../configure-apps/file-schema/startup/startup-element.md)

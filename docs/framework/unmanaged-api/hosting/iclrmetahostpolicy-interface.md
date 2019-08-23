---
title: ICLRMetaHostPolicy Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2735d3e0bbcb6326ca8ea87a3358824bca81108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951181"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy Arabirimi
Bir ilke ölçütlerine, yönetilen derlemeye, sürüme ve yapılandırma dosyasına dayalı ortak dil çalışma zamanı (CLR) arabirimine yönelik bir işaretçi döndüren [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan tercih edilen bir CLR arabirimi sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki kodda gösterildiği gibi [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini çağırarak, bu arabirime bir başvuru alabilirsiniz:  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> Bu arabirim gerçekte CLR 'yi yüklemez veya etkinleştirmez, ancak yalnızca yüklenmiş veya yüklenen kullanılabilir sürümlere göre tercih edilen CLR sürümünü döndürür.  
  
 .NET Framework 4 barındırma API 'SI ilkeleri birleştirir, böylece belirli ihtiyaçları olan konaklar, istenmeyen yaptırımlara gerek kalmadan temel işlevleri kullanabilir. Örneğin, bazı MSCorEE. dll dışarı aktarmaları belirli bir CLR 'ye bağlanır, ancak bir yöntem mantıksal olarak gerektirmeyebilir. [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırması, ana bilgisayarların çoğunluğu için ortak olan bağlama ilkeleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MetaHost. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

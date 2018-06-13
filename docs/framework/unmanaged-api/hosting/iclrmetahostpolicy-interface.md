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
ms.openlocfilehash: f9a70cf0812f84908630f109ef06aafa4b4f7525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434428"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy Arabirimi
Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) döndüren bir işaretçi bir ilke ölçütlere göre bir ortak dil çalışma zamanı (CLR) arabirimi, yöntem, yönetilen derleme, sürüm ve yapılandırma dosyası.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Tercih edilen bir CLR arabirimi ilke ölçütleri temel alarak, derleme, sürüm ve yapılandırma dosyası yönetilen sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim başvuru çağırarak alabilirsiniz [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev aşağıdaki kodda gösterildiği gibi:  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Bu arabirim gerçekten yük veya CLR, ancak yalnızca tercih edilen CLR sürümü yüklü ya da yüklenen kullanılabilir sürümlerine bağlı döndürür etkinleştirin.  
  
 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API barındırma birleştirir ilkeleri böylece ihtiyacınıza konaklarla temel işlevleri istenmeyen cezaları yansıtılmasını olmadan kullanabilir. Örneğin, bunu bir yöntem mantıksal olarak gerektirmeyebilecek ancak birçok MSCorEE.dll dışarı aktarmaları için belirli bir CLR, bağlarsınız. [Metahost_polıcy_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırması konakları çoğunluğu için ortak olan bağlama ilkeleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

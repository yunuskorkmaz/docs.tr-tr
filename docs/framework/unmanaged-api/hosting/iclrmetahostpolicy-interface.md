---
title: ICLRMetaHostPolicy Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8cbe1d397e1214cfa4d3f4cbc3d6cdf2d3ccd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy Arabirimi
Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) döndüren bir işaretçi bir ilke ölçütlere göre bir ortak dil çalışma zamanı (CLR) arabirimi, yöntem, yönetilen derleme, sürüm ve yapılandırma dosyası.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRequestedRuntime yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Tercih edilen bir CLR arabirimi ilke ölçütleri temel alarak, derleme, sürüm ve yapılandırma dosyası yönetilen sağlar.|  
  
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework 4 ve 4.5 eklenen CLR barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

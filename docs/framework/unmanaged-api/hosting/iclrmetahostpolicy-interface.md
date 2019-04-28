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
ms.openlocfilehash: 93507ac72b79210dc3a267fea39a6a7b2874916a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638703"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy Arabirimi
Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) ilke ölçütlere göre bir ortak dil çalışma zamanı (CLR) arabirim için bir işaretçi döndürür, yöntem, yönetilen derleme, sürüm ve yapılandırma dosyası.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Tercih edilen bir CLR arabirimi ilke ölçütlere göre derleme, sürüm ve yapılandırma dosyası yönetilen sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim için başvuru çağırarak alabilirsiniz [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev aşağıdaki kodda gösterildiği gibi:  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Bu arabirim gerçekten yüklemek veya CLR, ancak yalnızca tercih edilen CLR sürümü yüklü veya yüklenen kullanılabilir sürümler göre döndürür etkinleştirme.  
  
 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API'sini barındıran birleştirir ilkeleri böylece belirli gereksinimlere sahip konaklar istenmeyen yaptırımlara ödemeden temel işlevlerini kullanabilir. Örneğin, bir yöntem mantıksal olarak bunu gerekmese birçok MSCorEE.dll dışarı aktarmaları için belirli bir CLR, bağlayın. [Metahost_polıcy_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırma çoğunu konaklar için ortak olan bağlama ilkeleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

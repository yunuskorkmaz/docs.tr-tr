---
title: IHostAssemblyManager::GetNonHostStoreAssemblies Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6af013a833ae694aca991f9a71769869cc79b76b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies Metodu
Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) ortak dil çalışma zamanı (CLR) yüklemek için konak bekliyor derleme listesini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppReferenceList`  
 [out] Adresine bir işaretçi bir `ICLRAssemblyReferenceList` yüklemek için CLR konak bekliyor derlemelerine başvurular listesini içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen başvuruları listesini oluşturmak yeterli bellek yoktu `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR başvuru yönergeleri aşağıdaki kümesini kullanarak çözer:  
  
-   İlk olarak, listenin tarafından döndürülen derleme başvurularını danışır `GetNonHostStoreAssemblies`.  
  
-   Derleme listede görünüyorsa, CLR için normal olarak bağlar.  
  
-   Derleme listede görünmez ve ana bilgisayar uygulaması sağlamıştır [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR çağrıları [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) sağlamak konak izin vermek için bağlamak için derleme.  
  
-   Aksi takdirde, CLR derlemeye bağlamak başarısız olur.  
  
 Ana bilgisayar ayarlarsa `ppReferenceList` null, CLR ilk araştırmalar Genel Derleme Önbelleği çağrılar `ProvideAssembly`ve bir derleme başvurusu çözümlemek için uygulama temel araştırmaları.  
  
> [!NOTE]
>  Başlatma sırasında CLR çağırır `GetNonHostStoreAssemblies` yalnızca bir kez. Yöntem yeniden çağrılmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

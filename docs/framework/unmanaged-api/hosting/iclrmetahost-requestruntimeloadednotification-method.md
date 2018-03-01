---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi"
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
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7866270d8c9234a375401dfd05b504a06ddbf4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi
Ortak dil çalışma zamanı (CLR) sürüm ilk yüklendi, ancak henüz başlamamış çağrılacak garanti bir geri çağırma işlevi sağlar. Bu yöntem yerini [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCallbackFunction`  
 [in] Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pCallbackFunction`null şeklindedir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geri çağırma aşağıdaki şekilde çalışır:  
  
-   Yalnızca bir çalışma zamanı ilk kez yüklendiğinde geri çağırma çağrılır.  
  
-   Geri çağırma desteklemeyeceğini aynı çalışma zamanı yükler için çağrılır.  
  
-   Yeniden girme olmayan çalışma zamanı yükler için geri çağırma işlevi çağrıları serileştirilir.  
  
 Geri çağırma işlevi aşağıdaki prototipe sahiptir:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Geri çağırma işlev prototipleri aşağıdaki gibidir:  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Ana bilgisayar yüklenemiyor veya desteklemeyeceğini bir şekilde yüklenmesi başka bir çalışma zamanı neden çalışırsa `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` aşağıdaki şekilde geri işlevi kullanılması gereken sağlanan Parametreler:  
  
-   `pfnCallbackThreadSet`Bu tür bir yük denenmeden önce bir çalışma zamanı yüküne neden iş parçacığı tarafından çağrılmalıdır.  
  
-   `pfnCallbackThreadUnset`iş parçacığı artık böyle bir çalışma zamanı yükleme neden olur (ve ten ilk geri dönmeden önce) çağrılmalıdır.  
  
-   `pfnCallbackThreadSet`ve `pfnCallbackThreadUnset` hem de yeniden girme olmayan olması.  
  
> [!NOTE]
>  Ana bilgisayar uygulamaları değil çağırmalıdır `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` kapsamı dışında `pCallbackFunction` parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

---
title: ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87afb19736a484d24bde56cc34854dcd26c6b53b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755701"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi
Bir ortak dil çalışma zamanı (CLR) sürümünü ilk yüklendi, ancak henüz başlatılmadı çağrılacak garantili bir geri çağırma işlevini sağlar. Bu yöntem yerine geçer [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCallbackFunction`  
 [in] Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pCallbackFunction` NULL olur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geri çağırma şu şekilde çalışır:  
  
- Geri çağırma yalnızca bir çalışma zamanı ilk kez yüklendiğinde çağrılır.  
  
- Geri çağırma desteklemeyeceğini aynı çalışma zamanı yükler için çağrılmaz.  
  
- Reentrant olmayan çalışma zamanı yükler için geri çağırma işlevi için çağrı serileştirilir.  
  
 Geri çağırma işlevine aşağıdaki prototip sahiptir:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Geri arama işlev prototipleri aşağıdaki gibidir:  
  
- `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Konak yüklenemiyor veya yeniden girilen bir biçimde yüklenmesi başka bir çalışma zamanı neden planlıyorsa `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` geri aramada işlevi aşağıdaki şekilde kullanılmalıdır. sağlanan parametre:  
  
- `pfnCallbackThreadSet` Böyle bir yük denenmeden önce bir çalışma zamanı yükleme neden olabilecek bir iş parçacığı tarafından çağrılmalıdır.  
  
- `pfnCallbackThreadUnset` iş parçacığı artık böyle bir çalışma zamanı yükleme neden olur (ve ilk geri çağrısından döndürerek önce) çağrılmalıdır.  
  
- `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` reentrant olmayan olduğunda.  
  
> [!NOTE]
>  Ana bilgisayar uygulamaları gerekir çağrılmayan `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` kapsamı dışında `pCallbackFunction` parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)

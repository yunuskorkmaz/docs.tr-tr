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
ms.openlocfilehash: ac40e203cf7d32c1fe30c9915bac3171139403e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723291"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification Yöntemi

Ortak dil çalışma zamanı (CLR) sürümü ilk kez yüklendiğinde, ancak henüz başlamamışsa çağrılan bir geri çağırma işlevi sağlar. Bu yöntem [LockClrVersion](lockclrversion-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pCallbackFunction`  
 'ndaki Yeni bir çalışma zamanı yüklendiğinde çağrılan geri çağırma işlevi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pCallbackFunction` null.|  
  
## <a name="remarks"></a>Açıklamalar  

 Geri çağırma aşağıdaki şekilde işe yarar:  
  
- Geri çağırma yalnızca bir çalışma zamanı ilk kez yüklendiğinde çağrılır.  
  
- Aynı çalışma zamanının yer aldığı yük yükleri için geri çağırma çağrılmaz.  
  
- Yer suz çalışma zamanı yükleri için geri çağırma işlevine yapılan çağrılar serileştirilir.  
  
 Geri çağırma işlevi aşağıdaki prototiple sahiptir:  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Geri çağırma işlevi prototipleri aşağıdaki gibidir:  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Ana bilgisayar yüklemeyi amaçlıyordu veya başka bir çalışma zamanının yeniden eklenen bir şekilde yüklenmesine neden olursa, `pfnCallbackThreadSet` `pfnCallbackThreadUnset` geri çağırma işlevinde belirtilen ve parametreleri aşağıdaki şekilde kullanılmalıdır:  
  
- `pfnCallbackThreadSet` Bu tür bir yük denenerek çalışma zamanı yüküne neden olabilecek iş parçacığı tarafından çağrılmalıdır.  
  
- `pfnCallbackThreadUnset` iş parçacığı artık böyle bir çalışma zamanı yüküne (ve ilk geri aramadan dönmeden önce) neden olmaz çağrılmalıdır.  
  
- `pfnCallbackThreadSet` ve `pfnCallbackThreadUnset` her ikisi de yer yok.  
  
> [!NOTE]
> Konak uygulamalar `pfnCallbackThreadSet` `pfnCallbackThreadUnset` , parametre kapsamını çağırmamalıdır ve dışarıda olmamalıdır `pCallbackFunction` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Hosting](index.md)

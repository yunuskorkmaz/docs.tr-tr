---
description: ': ICLRRuntimeHost:: UnloadAppDomain yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeHost::UnloadAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: 2a47c6250434c3ee4122f8eeae75f25ee4c08a34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637293"
---
# <a name="iclrruntimehostunloadappdomain-method"></a>ICLRRuntimeHost::UnloadAppDomain Yöntemi

<xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen yönetilen öğesini kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwAppDomainId`  
 'ndaki Boşaltılacak uygulama etki alanının sayısal tanımlayıcısı.  
  
 `fWaitUntilDone`  
 [in] `true` ortak dil çalışma zamanının (CLR), uygulama etki alanını kaldırmayı denemeden önce uygulamanın geçerli iş parçacığını yürütmeyi bitirene kadar beklemesi gerektiğini belirtmek için.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`UnloadAppDomain` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, geçerli iş parçacığının yürütüldüğü uygulama etki alanının sayısal tanımlayıcısını alabilirsiniz. Bu tanımlayıcı, <xref:System.AppDomain.Id%2A> yönetilen türün özelliğine karşılık gelir <xref:System.AppDomain> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)

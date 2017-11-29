---
title: "ICLRRuntimeHost::ExecuteApplication Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteApplication
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3b43365ad208dae5b28b31cf494de37ca670d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication Yöntemi
ClickOnce dağıtım senaryolarında bildirimi tabanlı yeni bir etki alanına etkinleştirilmesi için uygulamayı belirtmek için kullanılır. Bu senaryolar hakkında daha fazla bilgi için bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzAppFullName`  
 [in] İçin tanımlanan uygulamasının tam adı <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] İçinde yer alan dizeleri sayısı `ppwzManifestPaths` dizi.  
  
 `ppwzManifestPaths`  
 [in] İsteğe bağlı. Uygulama için bildirim yolları içeren bir dize dizisi.  
  
 `dwActivationData`  
 [in] İçinde yer alan dizeleri sayısı `ppwzActivationData` dizi.  
  
 `ppwzActivationData`  
 [in] İsteğe bağlı. Web üzerinden dağıtılan uygulamalar için URL sorgu dizesi bölümünü gibi uygulamanın etkinleştirme verileri içeren bir dize dizisi.  
  
 `pReturnValue`  
 [out] Uygulama giriş noktasından döndürülen değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteApplication`ClickOnce uygulamaları yeni oluşturulan uygulama etki alanındaki etkinleştirmek için kullanılır.  
  
 `pReturnValue` Çıktı parametresi, uygulama tarafından döndürülen değer ayarlanır. Null değeri sağlarsanız `pReturnValue`, `ExecuteApplication` başarısız değil, ancak bir değer döndürmüyor.  
  
> [!IMPORTANT]
>  Çağırmayın [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce `ExecuteApplication` bildirimi tabanlı bir uygulama etkinleştirmek için yöntemi. Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [Iclrruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [SetAppDomainManager yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [İzlenecek yol: ClickOnce dağıtım Tasarımcısı'nı kullanarak API'si ile isteğe bağlı derlemeleri indirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)

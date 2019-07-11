---
title: ICLRRuntimeHost::ExecuteApplication Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8db6fd1296420011dcbfbbb0e5682f8a484dc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768818"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication Yöntemi
ClickOnce dağıtım senaryolarında bildirim tabanlı yeni bir etki alanı etkinleştirilmesi için uygulamayı belirtmek için kullanılır. Bu senaryolar hakkında daha fazla bilgi için bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzAppFullName`  
 [in] İçin tanımlandığı gibi uygulamanın tam adını <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] Dize içindeki sayısı `ppwzManifestPaths` dizisi.  
  
 `ppwzManifestPaths`  
 [in] İsteğe bağlı. Uygulama için bildirim yolları içeren bir dize dizisi.  
  
 `dwActivationData`  
 [in] Dize içindeki sayısı `ppwzActivationData` dizisi.  
  
 `ppwzActivationData`  
 [in] İsteğe bağlı. Web üzerinden dağıtılan uygulamalar için URL sorgu dizesi kısmı gibi uygulamanın etkinleştirme verileri içeren bir dize dizisi.  
  
 `pReturnValue`  
 [out] Uygulamanın giriş noktasından döndürülen değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteApplication` Yeni oluşturulan uygulama etki alanındaki ClickOnce uygulamaları etkinleştirmek için kullanılır.  
  
 `pReturnValue` Çıkış parametresi uygulama tarafından döndürülen değere ayarlanır. Null değeri sağlarsanız `pReturnValue`, `ExecuteApplication` başarısız olmaz, ancak bir değer döndürmez.  
  
> [!IMPORTANT]
>  Çağırmayın [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce `ExecuteApplication` bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemi. Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)

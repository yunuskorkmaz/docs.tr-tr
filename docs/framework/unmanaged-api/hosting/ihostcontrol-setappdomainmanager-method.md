---
title: IHostControl::SetAppDomainManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb63f1e9d2b30ce764521aa68fbafe0407cbe922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441880"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager Yöntemi
Ana uygulama etki alanı oluşturulduğunu size bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwAppDomainID`  
 [in] Seçili sayısal tanımlayıcı <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [in] Bir işaretçi <xref:System.AppDomainManager> olarak ana bilgisayar uygulayan nesne `IUnknown`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.AppDomainManager> Yönetilen koda bootstrap ve oluşturulması ve her birinin ayarlarını denetlemek için bir mekanizma ile ana bilgisayarının sağladığı <xref:System.AppDomain>. <xref:System.AppDomainManager> Her yüklenir <xref:System.AppDomain> olduğunda, <xref:System.AppDomain> oluşturulur. Seçerse, CLR ana uygulama etki alanı değerini ayarlayarak oluşturuldu bildirir `pUnkAppDomainManager` parametresi.  
  
 Uygulamaya `SetAppDomainManager` yöntemi, ana bilgisayar ayarlayabilirsiniz derleme adı ve türü için uygulama etki alanı yöneticisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

---
description: ': IHostControl:: SetAppDomainManager yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1fc5efc0afad73d1805338140f186a50913ca542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708908"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager Yöntemi

Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwAppDomainID`  
 'ndaki Seçili öğesinin sayısal tanımlayıcısı <xref:System.AppDomain> .  
  
 `pUnkAppDomainManager`  
 'ndaki <xref:System.AppDomainManager> Konağın uyguladığı nesneye yönelik bir işaretçi `IUnknown` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 , <xref:System.AppDomainManager> Ana bilgisayarı yönetilen koda önyükleme yapmak ve her birinin oluşturma ve ayarlarını denetlemek için bir mekanizmaya sahip sağlar <xref:System.AppDomain> . , <xref:System.AppDomainManager> Oluşturulduğunda her birine yüklenir <xref:System.AppDomain> <xref:System.AppDomain> . Seçerse, CLR, parametrenin değerini ayarlayarak ana bilgisayara uygulama etki alanının oluşturulduğunu bildirir `pUnkAppDomainManager` .  
  
 `SetAppDomainManager`Yöntemi, uygulama etki alanı yöneticisinin derleme adını ve türünü ayarlayabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl Arabirimi](ihostcontrol-interface.md)

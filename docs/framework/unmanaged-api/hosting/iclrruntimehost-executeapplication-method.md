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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965351"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication Yöntemi
Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır. Bu senaryolar hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
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
 'ndaki Uygulamanın tanımlandığı <xref:System.ApplicationIdentity>şekliyle tam adı.  
  
 `dwManifestPaths`  
 'ndaki `ppwzManifestPaths` Dizide bulunan dizelerin sayısı.  
  
 `ppwzManifestPaths`  
 'ndaki Seçim. Uygulamanın bildirim yollarını içeren bir dize dizisi.  
  
 `dwActivationData`  
 'ndaki `ppwzActivationData` Dizide bulunan dizelerin sayısı.  
  
 `ppwzActivationData`  
 'ndaki Seçim. Web üzerinde dağıtılan uygulamalar için URL 'nin sorgu dizesi kısmı gibi uygulamanın etkinleştirme verilerini içeren bir dize dizisi.  
  
 `pReturnValue`  
 dışı Uygulamanın giriş noktasından döndürülen değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteApplication`, yeni oluşturulan bir uygulama etki alanında ClickOnce uygulamalarını etkinleştirmek için kullanılır.  
  
 `pReturnValue` Output parametresi, uygulama tarafından döndürülen değere ayarlanır. `pReturnValue` İçin`ExecuteApplication` null değeri sağlarsanız, başarısız olmaz, ancak bir değer döndürmez.  
  
> [!IMPORTANT]
> Bildirim tabanlı bir uygulamayı etkinleştirmek için `ExecuteApplication` yöntemini çağırmadan önce [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemini çağırmayın. Yöntemi ilk kez `ExecuteApplication` çağrılırsa Yöntem çağrısı başarısız olur. `Start`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MSCorEE. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [SetAppDomainManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)

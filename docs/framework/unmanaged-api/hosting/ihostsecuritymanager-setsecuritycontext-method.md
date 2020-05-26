---
title: IHostSecurityManager::SetSecurityContext Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 79ef08ef70ad1132ceacc3e2b997651e57032b9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803819"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext Yöntemi
Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `eContextType`  
 'ndaki Ortak dil çalışma zamanının (CLR) konağa ne tür bir içerik yerleştirmekte olduğunu gösteren [EContextType](econtexttype-enumeration.md) değerlerinden biri.  
  
 `ppSecurityContext`  
 dışı Yeni bir [IHostSecurityContext](ihostsecuritycontext-interface.md) nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `SetSecurityContext`Çeşitli SENARYOLARDA clr çağrıları. Sınıfı ve modül oluşturucularını ve sonlandırıcıları yürütmeden önce CLR, `SetSecurityContext` Konağı yürütme hatalarından korumak için çağırır. Daha sonra, başka bir çağrısı kullanarak, oluşturucunun veya sonlandırıcının yürütülmesi sonrasında güvenlik bağlamını özgün durumuna sıfırlar `SetSecurityContext` . G/ç tamamlanırken benzer bir model oluşur. Ana bilgisayar [ıhostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)'ı uygularsa, `SetSecurityContext` ana bilgisayar [ıclriocompletionmanager:: ONTAMAMLANMıŞTıR](iclriocompletionmanager-oncomplete-method.md)öğesini çağırarak clr çağrıları.  
  
 Çalışan iş parçacıklarında zaman uyumsuz noktalarda, CLR 'nin `SetSecurityContext` veya <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> clr 'nin iş parçacığı havuzunu yapıp uygulamadığına bağlı olarak [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)içindeki veya içinde clr çağrıları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType Sabit Listesi](econtexttype-enumeration.md)
- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
- [IHostSecurityContext Arabirimi](ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)

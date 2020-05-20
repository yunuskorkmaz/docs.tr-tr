---
title: ICLRControl::GetCLRManager Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615859"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager Yöntemi
Konağın ortak dil çalışma zamanını (CLR) yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki `IID`Döndürülecek yönetici türü. Aşağıdaki `IID` değerler desteklenir.  
  
- IID_ICLRDebugManager: `ppObject` [ICLRDebugManager](iclrdebugmanager-interface.md)türünden olacağını belirtir.  
  
- IID_ICLRErrorReportingManager: `ppObject` [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)türünden olacağını belirtir.  
  
- IID_ICLRGCManager: `ppObject` [ICLRGCManager](iclrgcmanager-interface.md)türünden olacağını belirtir.  
  
- IID_ICLRHostProtectionManager: `ppObject` [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)türünde olacağını belirtir.  
  
- IID_ICLROnEventManager: `ppObject` [ICLROnEventManager](iclroneventmanager-interface.md)türünden olacağını belirtir.  
  
- IID_ICLRPolicyManager: `ppObject` [ICLRPolicyManager](iclrpolicymanager-interface.md)türünde olacağını belirtir.  
  
- IID_ICLRTaskManager: `ppObject` [ICLRTaskManager](iclrtaskmanager-interface.md)türünden olacağını belirtir.  
  
 `ppObject`  
 dışı İstenen yöneticinin arabirim işaretçisi veya geçersiz bir yönetici türü isteniyorsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOINTERFACE|Arabirim türü desteklenmiyor.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [IHostControl Arabirimi](ihostcontrol-interface.md)

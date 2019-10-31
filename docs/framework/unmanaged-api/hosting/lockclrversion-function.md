---
title: LockClrVersion İşlevi
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133772"
---
# <a name="lockclrversion-function"></a>LockClrVersion İşlevi
Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hostCallback`  
 'ndaki Başlatma sonrasında CLR tarafından çağrılacak işlev.  
  
 `pBeginHostSetup`  
 'ndaki Başlatmanın başladığı CLR 'yi bilgilendirmek için konak tarafından çağrılacak işlev.  
  
 `pEndHostSetup`  
 'ndaki Başlatma işleminin tamamlandığını CLR bilgilendirmek için konak tarafından çağrılacak işlev.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|Bağımsız değişkenlerden biri veya birkaçı null.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, CLR 'yi başlatmadan önce `LockClrVersion` çağırır. `LockClrVersion`, tümü [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır. Bu tür aşağıdaki gibi tanımlanır.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:  
  
1. Konak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır. Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.  
  
2. Çalışma zamanı, `hostCallback` parametresi tarafından belirtilen işlevi çağırır.  
  
3. `hostCallback` tarafından belirtilen işlev, aşağıdaki çağrı dizisini yapar:  
  
    - `pBeginHostSetup` parametresi tarafından belirtilen işlev.  
  
    - `CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).  
  
    - [ICLRRuntimeHost:: SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    - `pEndHostSetup` parametresi tarafından belirtilen işlev.  
  
 `pEndHostSetup` `pBeginHostSetup` olan tüm çağrılar, aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir. Bu iş parçacığı `hostCallback` çağrıldığı iş parçacığından farklı olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

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
ms.openlocfilehash: 2ff08ec8f194ccc9e968b3a7ee017afe788f4b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704948"
---
# <a name="lockclrversion-function"></a>LockClrVersion İşlevi

Konağın, CLR 'yi açıkça başlatmadan önce işlem içinde ortak dil çalışma zamanının (CLR) hangi sürümünün kullanılacağını belirlemesine izin verir.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 CLR başlatmadan önce konak çağırır `LockClrVersion` . `LockClrVersion` tümü [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)türünde geri çağırmalar olan üç parametre alır. Bu tür aşağıdaki gibi tanımlanır.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Çalışma zamanının başlatılması sırasında aşağıdaki adımlar oluşur:  
  
1. Konak [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya diğer çalışma zamanı başlatma işlevlerinden birini çağırır. Alternatif olarak, ana bilgisayar COM nesne etkinleştirmesini kullanarak çalışma zamanını başlatabilir.  
  
2. Çalışma zamanı, parametresi tarafından belirtilen işlevi çağırır `hostCallback` .  
  
3. Daha sonra belirtilen işlev `hostCallback` aşağıdaki çağrı dizisini yapar:  
  
    - Parametresi tarafından belirtilen işlev `pBeginHostSetup` .  
  
    - `CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).  
  
    - [ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).  
  
    - Parametresi tarafından belirtilen işlev `pEndHostSetup` .  
  
 ' Den ' e yapılan tüm çağrılar, `pBeginHostSetup` `pEndHostSetup` aynı mantıksal yığın ile tek bir iş parçacığında veya fiber üzerinde gerçekleşmelidir. Bu iş parçacığı, üzerinde çağrılan iş parçacığından farklı olabilir `hostCallback` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)

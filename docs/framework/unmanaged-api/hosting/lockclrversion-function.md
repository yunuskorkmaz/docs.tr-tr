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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91bb1a9416e577dbb5cc96e8be87033c53232811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765277"
---
# <a name="lockclrversion-function"></a>LockClrVersion İşlevi
Ortak dil çalışma zamanı (CLR) hangi sürümünün işlem dahilinde CLR açıkça başlatılmadan önce kullanılacağını belirlemek için ana sağlar.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hostCallback`  
 [in] CLR başlatma sırasında tarafından çağrılacak işlev.  
  
 `pBeginHostSetup`  
 [in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev başlatılıyor.  
  
 `pEndHostSetup`  
 [in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev tamamlanmıştır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|Bir veya daha fazla bağımsız değişken NULL'dur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak çağrıları `LockClrVersion` CLR başlatma önce. `LockClrVersion` geri çağırmaları türünün her biri, üç parametre almayan [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Bu tür şu şekilde tanımlanır.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Aşağıdaki adımlar, çalışma zamanı başlatma sırasında gerçekleşir:  
  
1. Konak çağrıları [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya bir çalışma zamanı başlatma işlevlerden biri. Alternatif olarak, konak COM Nesne etkinleştirmesi kullanarak çalışma zamanı başlatabilir.  
  
2. Çalışma zamanı tarafından belirtilen işlev çağrıları `hostCallback` parametresi.  
  
3. Tarafından belirtilen işlevin `hostCallback` sonra sırasıyla aşağıdaki çağrıları yapar:  
  
    - Tarafından belirtilen işlevin `pBeginHostSetup` parametresi.  
  
    - `CorBindToRuntimeEx` (veya başka bir çalışma zamanı başlatma işlevi).  
  
    - [Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    - [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    - Tarafından belirtilen işlevin `pEndHostSetup` parametresi.  
  
 Tüm çağrıların `pBeginHostSetup` için `pEndHostSetup` tek iş parçacığı veya aynı mantıksal yığınına sahip bir fiber gerçekleşmemelidir. Bu iş parçacığının iş parçacığı alacağı farklı `hostCallback` çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

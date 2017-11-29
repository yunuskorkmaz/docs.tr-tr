---
title: "LockClrVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be41ae47f78a41e2f2be10a1e38d938dde9a4701
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lockclrversion-function"></a>LockClrVersion İşlevi
CLR açıkça başlatmadan önce işlemi içinde ortak dil çalışma zamanı (CLR) hangi sürümünün kullanılacağını belirlemek için ana sağlar.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hostCallback`  
 [in] Başlatma sırasında CLR tarafından çağrılacak işlev.  
  
 `pBeginHostSetup`  
 [in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev başlatılıyor.  
  
 `pEndHostSetup`  
 [in] Bu başlatma CLR bilgilendirmek için ana bilgisayar tarafından çağrılacak işlev tamamlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart COM hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|Bir veya daha fazla bağımsız değişken null şeklindedir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar çağrıları `LockClrVersion` CLR başlatma önce. `LockClrVersion`tümü geri aramalar türü üç parametre alır [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Bu tür şu şekilde tanımlanır.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Aşağıdaki adımlar, çalışma zamanı modülü başlatma sırasında gerçekleşir:  
  
1.  Ana bilgisayar çağrıları [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya bir çalışma zamanı başlatma işlevleri biri. Alternatif olarak, konak COM Nesne etkinleştirmesi kullanarak çalışma zamanı başlatabilir.  
  
2.  Çalışma zamanı tarafından belirtilen işlevi çağırır `hostCallback` parametresi.  
  
3.  Tarafından belirtilen işlevin `hostCallback` çağrıları aşağıdaki dizisi hale getirir:  
  
    -   Tarafından belirtilen işlevin `pBeginHostSetup` parametresi.  
  
    -   `CorBindToRuntimeEx`(veya başka bir çalışma zamanı başlatma işlevi).  
  
    -   [Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   Tarafından belirtilen işlevin `pEndHostSetup` parametresi.  
  
 Gelen tüm çağrıları `pBeginHostSetup` için `pEndHostSetup` tek iş parçacığı veya fiber aynı mantıksal yığınına sahip olmalıdır. Bu iş parçacığı iş parçacığı üzerine farklı olabilir `hostCallback` olarak adlandırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

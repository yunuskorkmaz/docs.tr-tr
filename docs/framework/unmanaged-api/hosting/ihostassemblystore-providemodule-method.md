---
title: IHostAssemblyStore::ProvideModule Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599354"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule Yöntemi
Modül bir derleme veya bağlı (ancak değil bir katıştırılmış) içinde kaynak dosyası çözümler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBindInfo`  
 [in] Bir işaretçi bir [Modulebindınfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) istenen modülün açıklayan örneği <xref:System.AppDomain>, derleme ve modül adı.  
  
 `pdwModuleId`  
 [out] Bir işaretçi için benzersiz bir tanımlayıcıya `IStream` içeren yüklenen modül.  
  
 `ppStmModuleImage`  
 [out] Adresine bir işaretçi bir `IStream` yüklenmesi için taşınabilir yürütülebilir (PE) görüntüsünü içeren, nesne veya modülü bulunamadı yoksa null.  
  
 `ppStmPDB`  
 [out] Adresine bir işaretçi bir `IStream` nesne, istenen modülü için program hata ayıklama (PDB) bilgilerini içeren veya .pdb dosyası bulunamadı, null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideModule` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme veya bağlı kaynak bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` döndürülecek konak istediği tanımlayıcı içerecek yeteri kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kimlik değeri için döndürülen `pdwModuleId` ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlem yaşam süresi içinde benzersiz olmalıdır. CLR, ilişkili akış için benzersiz tanımlayıcı olarak bu değeri kullanır. Her değer değerlerini karşı denetler `pAssemblyId` yapılan çağrılar tarafından döndürülen [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ve değerlerini karşı `pdwModuleId` yapılan diğer çağrılar tarafından döndürülen `ProvideModule`. Konak için başka aynı tanımlayıcı değerini döndürürse `IStream`, CLR, akış içeriğini zaten eşlendi olup olmadığını denetler. Bu durumda, CLR görüntü yerine yeni bir eşleme var olan kopyasını yükler. Bu nedenle, tanımlayıcı da döndürüldüğü derleme tanımlayıcıları ile örtüşmemelidir `ProvideAssembly`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

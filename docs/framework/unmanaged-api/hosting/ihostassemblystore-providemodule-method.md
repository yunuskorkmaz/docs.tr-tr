---
title: "IHostAssemblyStore::ProvideModule Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8b29f19933ae985d15627d1eba2622f350a52e72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule Yöntemi
Modül bir derlemeyi ya da bağlı (ancak olmayan bir katıştırılmış) içinde kaynak dosyası çözümler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBindInfo`  
 [in] Bir işaretçi bir [Modulebindınfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) istenen modülünün açıklar örneği <xref:System.AppDomain>, derleme ve modül adı.  
  
 `pdwModuleId`  
 [out] İçin benzersiz bir tanımlayıcı için bir işaretçi `IStream` içeren yüklenen modül.  
  
 `ppStmModuleImage`  
 [out] Adresine bir işaretçi bir `IStream` nesnesi, yüklenecek taşınabilir yürütülebilir (PE) görüntüsünü içeren veya modül bulunamadı, boş.  
  
 `ppStmPDB`  
 [out] Adresine bir işaretçi bir `IStream` nesne, istenen modülünün program hata ayıklama (PDB) bilgilerini içeren veya .pdb dosyasını bulunamadı yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideModule`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0X80070002)|İstenen derlemeyi ya da bağlı kaynak bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`döndürülecek konak istediği tanımlayıcı içerecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin kimlik değeri döndürülen `pdwModuleId` ana bilgisayar tarafından belirtilir. Tanımlayıcıları bir işlem yaşam süresi içinde benzersiz olmalıdır. CLR ilişkili akışı için benzersiz tanımlayıcı olarak bu değeri kullanır. Her değer için değerleri karşı denetler `pAssemblyId` çağrı tarafından döndürülen [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ve değerlerini karşı `pdwModuleId` diğer çağrı tarafından döndürülen `ProvideModule`. Ana bilgisayar aynı tanımlayıcısı değeri için başka bir döndürürse `IStream`, CLR, akış içeriğini zaten eşlenmiş olup olmadığını denetler. Bu durumda, CLR var olan kopyasını yeni bir eşleme yerine görüntüsü yükler. Bu nedenle, tanımlayıcı ayrıca döndürülen derleme tanımlayıcıları ile çakışmaması gerekir `ProvideAssembly`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

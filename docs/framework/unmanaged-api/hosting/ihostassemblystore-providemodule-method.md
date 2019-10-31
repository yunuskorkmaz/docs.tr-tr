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
ms.openlocfilehash: eed09a8149a21140ad61133f29391f86cb0fb929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124466"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule Yöntemi
Derleme içindeki bir modülü veya bağlı (gömülü) bir kaynak dosyasını çözer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBindInfo`  
 'ndaki İstenen modülün <xref:System.AppDomain>, bütünleştirilmiş kodu ve modül adını açıklayan bir [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) örneği işaretçisi.  
  
 `pdwModuleId`  
 dışı Yüklenen modülü içeren `IStream` için benzersiz bir tanımlayıcı işaretçisi.  
  
 `ppStmModuleImage`  
 dışı Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren `IStream` nesnesinin adresine yönelik bir işaretçi veya modül bulunamazsa null.  
  
 `ppStmPDB`  
 dışı İstenen modüle yönelik program hata ayıklama (PDB) bilgilerini içeren `IStream` nesnesinin adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideModule` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme veya bağlı kaynak bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`, konağın döndürmek istediği tanımlayıcıyı içerecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 `pdwModuleId` için döndürülen kimlik değeri ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır. CLR bu değeri ilişkili akış için benzersiz tanımlayıcı olarak kullanır. Her bir değeri, [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) çağrıları tarafından döndürülen `pAssemblyId` değerlerine ve diğer `ProvideModule`yapılan çağrılar tarafından döndürülen `pdwModuleId` değerlere karşı denetler. Ana bilgisayar başka bir `IStream`için aynı tanımlayıcı değerini döndürürse, CLR bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler. Bu durumda, CLR yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler. Bu nedenle, tanımlayıcı aynı zamanda `ProvideAssembly`döndürülen derleme tanımlayıcılarıyla çakışmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

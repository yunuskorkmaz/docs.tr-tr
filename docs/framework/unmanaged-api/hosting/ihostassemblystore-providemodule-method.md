---
description: 'Şu konuda daha fazla bilgi edinin: IHostAssemblyStore::P rovideModule yöntemi'
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
ms.openlocfilehash: 9e783b9f8db303d095995507689d7567225a51fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709034"
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
 'ndaki İstenen modülün [](modulebindinfo-structure.md) <xref:System.AppDomain> , derlemenin ve modül adının açıklandığı bir ModuleBindInfo örneği işaretçisi.  
  
 `pdwModuleId`  
 dışı Yüklenen modülün bulunduğu bir benzersiz tanımlayıcı işaretçisi `IStream` .  
  
 `ppStmModuleImage`  
 dışı `IStream` Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir nesnenin adresine yönelik bir işaretçi veya modül bulunamazsa null.  
  
 `ppStmPDB`  
 dışı `IStream` İstenen modüle yönelik program hata ayıklama (pdb) bilgilerini içeren nesnenin adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideModule` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme veya bağlı kaynak bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` , konağın döndürmek istediği tanımlayıcıyı içerecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  

 İçin döndürülen kimlik değeri `pdwModuleId` ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır. CLR bu değeri ilişkili akış için benzersiz tanımlayıcı olarak kullanır. Her bir değeri `pAssemblyId` , [ProvideAssembly](ihostassemblystore-provideassembly-method.md) çağrıları tarafından döndürülen değerlere ve `pdwModuleId` diğer çağrıları tarafından döndürülen değerlere karşı denetler `ProvideModule` . Konak diğeri için aynı tanımlayıcı değerini döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler. Bu durumda, CLR yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler. Bu nedenle, tanımlayıcı aynı zamanda öğesinden döndürülen derleme tanımlayıcılarıyla çakışmamalıdır `ProvideAssembly` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)

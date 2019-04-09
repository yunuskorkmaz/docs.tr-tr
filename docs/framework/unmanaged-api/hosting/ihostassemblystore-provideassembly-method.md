---
title: IHostAssemblyStore::ProvideAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111910"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly Yöntemi
Tarafından başvurulmuyor bir derlemeye bir başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) sağlayıcıdan döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Ortak dil çalışma zamanı (CLR) çağıran `ProvideAssembly` listesinde görünmüyor her derleme için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBindInfo`  
 [in] Bir işaretçi bir [Assemblybindınfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) varlığı veya yokluğu herhangi bir sürüm oluşturma ilkesine dahil olmak üzere, belirli bir bağlama özellikleri belirlemek için konağın kullandığı örneği ve bağlamak için hangi derleme.  
  
 `pAssemblyId`  
 [out] Bunun için istenen derleme için benzersiz bir tanımlayıcı için bir işaretçi `IStream`.  
  
 `pHostContext`  
 [out] Bir platform gerek olmadan istenen derleme kanıtı belirlemek için kullanılan ana bilgisayara özgü veri işaretçisi çağrısı çağırın. `pHostContext` karşılık gelen <xref:System.Reflection.Assembly.HostContext%2A> yönetilen özellik <xref:System.Reflection.Assembly> sınıfı.  
  
 `ppStmAssemblyImage`  
 [out] Adresine bir işaretçi bir `IStream` yüklenmesi veya bütünleştirilmiş kod bulunamadı, null için taşınabilir yürütülebilir (PE) görüntüsünü içerir.  
  
 `ppStmPDB`  
 [out] Adresine bir işaretçi bir `IStream` varsa program hata ayıklama (PDB) bilgileri veya null .pdb dosyası bulunamadı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|Tarafından belirtilen arabellek boyutu `pAssemblyId` döndürülecek konak istediği tanımlayıcısı tutabilecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kimlik değeri için döndürülen `pAssemblyId` ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlem yaşam süresi içinde benzersiz olmalıdır. CLR, akışı için benzersiz bir tanımlayıcı olarak bu değeri kullanır. Her değer değerlerini karşı denetler `pAssemblyId` yapılan diğer çağrılar tarafından döndürülen `ProvideAssembly`. Konak aynı döndürürse `pAssemblyId` başka bir değer `IStream`, CLR, akış içeriğini zaten eşlendi olup olmadığını denetler. Bu durumda, çalışma zamanı yerine yeni bir eşleme görüntü kopyasının yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

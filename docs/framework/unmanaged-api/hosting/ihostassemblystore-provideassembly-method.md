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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124482"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly Yöntemi
[IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)öğesinden döndürülen [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır. Ortak dil çalışma zamanı (CLR), listede görünmeyen her derleme için `ProvideAssembly` çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Herhangi bir sürüm oluşturma ilkesinin varlığı veya yokluğu ve hangi derlemenin bağlanacağı dahil olmak üzere, konağın belirli bağlama özelliklerini belirlemede kullandığı bir [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) örneği işaretçisi.  
  
 `pAssemblyId`  
 dışı Bu `IStream`için istenen derleme için benzersiz bir tanımlayıcı işaretçisi.  
  
 `pHostContext`  
 dışı Platform çağırma çağrısına gerek olmadan istenen derlemenin kanıtını belirlemede kullanılan, konağa özgü verilere yönelik bir işaretçi. `pHostContext`, yönetilen <xref:System.Reflection.Assembly> sınıfının <xref:System.Reflection.Assembly.HostContext%2A> özelliğine karşılık gelir.  
  
 `ppStmAssemblyImage`  
 dışı Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren `IStream` adresine yönelik bir işaretçi veya derleme bulunamazsa null.  
  
 `ppStmPDB`  
 dışı Program hata ayıklama (PDB) bilgilerini içeren `IStream` adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|`pAssemblyId` tarafından belirtilen arabellek boyutu, konağın döndürmek istediği tanımlayıcıyı tutabilecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 `pAssemblyId` için döndürülen kimlik değeri ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır. CLR bu değeri akış için benzersiz bir tanımlayıcı olarak kullanır. Her değeri, `ProvideAssembly`için diğer çağrılar tarafından döndürülen `pAssemblyId` değerlere karşı denetler. Ana bilgisayar başka bir `IStream`için aynı `pAssemblyId` değerini döndürürse, CLR bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler. Öyleyse, çalışma zamanı yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

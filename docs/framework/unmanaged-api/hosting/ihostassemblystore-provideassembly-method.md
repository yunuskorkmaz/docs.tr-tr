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
ms.openlocfilehash: 162def0d703ea81efc3df3ea5ee08b58e34822e6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501579"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly Yöntemi
[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)öğesinden döndürülen [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır. Ortak dil çalışma zamanı (CLR), `ProvideAssembly` Listede görünmeyen her derleme için çağırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Herhangi bir sürüm oluşturma ilkesinin varlığı veya yokluğu ve hangi derlemenin bağlanacağı dahil olmak üzere, konağın belirli bağlama özelliklerini belirlemede kullandığı bir [AssemblyBindInfo](assemblybindinfo-structure.md) örneği işaretçisi.  
  
 `pAssemblyId`  
 dışı Bunun için istenen derleme için benzersiz bir tanımlayıcı işaretçisi `IStream` .  
  
 `pHostContext`  
 dışı Platform çağırma çağrısına gerek olmadan istenen derlemenin kanıtını belirlemede kullanılan, konağa özgü verilere yönelik bir işaretçi. `pHostContext`<xref:System.Reflection.Assembly.HostContext%2A>yönetilen sınıfın özelliğine karşılık gelir <xref:System.Reflection.Assembly> .  
  
 `ppStmAssemblyImage`  
 dışı `IStream`Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir adresine yönelik bir işaretçi veya derleme bulunamazsa null.  
  
 `ppStmPDB`  
 dışı `IStream`Program hata ayıklama (pdb) bilgilerini içeren bir adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|COR_E_FILENOTFOUND (0x80070002)|İstenen derleme bulunamadı.|  
|E_NOT_SUFFICIENT_BUFFER|Tarafından belirtilen arabellek boyutu, `pAssemblyId` konağın döndürmek istediği tanımlayıcıyı tutabilecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin döndürülen kimlik değeri `pAssemblyId` ana bilgisayar tarafından belirtilir. Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır. CLR bu değeri akış için benzersiz bir tanımlayıcı olarak kullanır. Her değeri, `pAssemblyId` için diğer çağrılar tarafından döndürülen değerlere karşı denetler `ProvideAssembly` . Konak `pAssemblyId` diğeri için aynı değeri döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler. Öyleyse, çalışma zamanı yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)

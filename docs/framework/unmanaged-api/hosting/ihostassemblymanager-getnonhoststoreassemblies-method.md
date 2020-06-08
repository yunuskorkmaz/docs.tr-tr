---
title: IHostAssemblyManager::GetNonHostStoreAssemblies Metodu
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: 9a1440be7011130b16d7112ae15026eb74856190
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501605"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies Metodu
Konağın ortak dil çalışma zamanı (CLR) yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppReferenceList`  
 dışı `ICLRAssemblyReferenceList`KONAĞıN clr 'nin yüklenmesini beklediği derlemelere yönelik başvuruların listesini içeren adresinin bir işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen için başvuruların listesini oluşturmak üzere yeterli kullanılabilir bellek yoktu `ICLRAssemblyReferenceList` .|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, aşağıdaki kılavuz kümesini kullanarak başvuruları çözümler:  
  
- İlk olarak, tarafından döndürülen derleme başvuruları listesini inceleyerek `GetNonHostStoreAssemblies` .  
  
- Derleme listede görünürse, CLR buna normal olarak bağlanır.  
  
- Derleme listede görünmezse ve konak [IHostAssemblyStore](ihostassemblystore-interface.md)'un bir uygulamasını SAĞLADıYSA, clr 'nin bağlanacak derlemeyi sağlaması Için [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) ' ı çağırır.  
  
- Aksi takdirde, CLR derlemeye bağlanamaz.  
  
 Konak `ppReferenceList` null olarak ayarlanırsa, clr ilk olarak genel derleme önbelleğini yoklamalar, çağırır `ProvideAssembly` ve ardından derleme başvurusunu çözümlemek için uygulama temelini yoklamalar.  
  
> [!NOTE]
> Başlatma sonrasında CLR `GetNonHostStoreAssemblies` yalnızca bir kez çağrı yapılır. Yöntemi yeniden çağrılmadı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)

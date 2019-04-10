---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d6f93ee7870c9d81394ee55c5574c52c2aea50a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223127"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a>ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi
Bir işaretçi alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen akış derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStream`  
 [in] Bir arabirim işaretçisi için bir `IStream` değerlendirilecek derlemeyi içeren.  
  
 `dwFlags`  
 [in] Sonra genişletilebilmek için sağlanır. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.  
  
 `pExcludeAssembliesList`  
 [in] Bir işaretçi bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) dışında tutulan derlemeler için derleme kimlik verilerini içeren nesne `ppReferenceEnum`.  
  
 `ppReferenceEnum`  
 [out] Adresine bir işaretçi bir `ICLRReferenceAssemblyEnum` derlemesinde tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne `pStream`, derlemeleri hariç `pExcludeAssembliesList`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntemi başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Arayan, döndürülen listeden bir dizi bilinen bütünleştirilmiş kod başvuruları dışlanacak seçebilirsiniz. Bu tarafından tanımlanan `pExcludeAssembliesList`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

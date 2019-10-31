---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 65dc330e88cb2457cc34f9994313373ab1ab84aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126698"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a>ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi
Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFilePath`  
 'ndaki Değerlendirilecek derlemenin yolu.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için verilmiştir. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.  
  
 `pExcludeAssembliesList`  
 'ndaki `ppReferenceEnum`dışında tutulması gereken derlemeleri temsil eden [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) nesnesine yönelik bir işaretçi.  
  
 `ppReferenceEnum`  
 dışı `pExcludeAssembliesList`tarafından temsil edilen derlemeler hariç `pwzFilePath`derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren `ICLRReferenceAssemblyEnum` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağıran, bir bilinen derleme başvuruları kümesini döndürülen listeden dışlamayı tercih edebilir. Bu küme `pExcludeAssembliesList` parametresi tarafından tanımlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

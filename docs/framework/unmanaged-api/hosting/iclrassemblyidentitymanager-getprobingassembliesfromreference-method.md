---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 21ebd0c64d6c8bbdac327258ad4c7ffec83a1ce9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504322"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a>ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi
Belirtilen kimlik türüyle derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwMachineType`  
 'ndaki WinNT. h içinde tanımlanan işlemci mimarisini belirten geçerli bir değer.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için verilmiştir. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.  
  
 `pwzReferenceIdentity`  
 'ndaki Genellikle [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) veya [ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metoduna yapılan çağrıdan döndürülen donuk bir derleme bağlama kimliği.  
  
 `ppProbingAssemblyEnum`  
 dışı `ICLRProbingAssemblyEnum`Tarafından tanımlanan derlemenin başvurduğu derlemelere yönelik başvuruları içeren bir Numaralandırıcı için arabirim işaretçisi `pwzReferenceIdentity` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum Arabirimi](iclrprobingassemblyenum-interface.md)

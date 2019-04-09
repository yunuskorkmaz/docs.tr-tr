---
title: GetRequestedRuntimeInfo İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1290aa864a3f65e549bc26173dcd23648b8dee90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074891"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo İşlevi
Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürümünü ve dizin bilgilerini alır.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pExe`  
 [in] Uygulamanın adı.  
  
 `pwszVersion`  
 [in] Çalışma zamanı sürüm numarasını belirten bir dize.  
  
 `pConfigurationFile`  
 [in] İle ilişkili yapılandırma dosyasının adını `pExe`.  
  
 `startupFlags`  
 [in] Bir veya daha fazla [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi değerleri.  
  
 `runtimeInfoFlags`  
 [in] Bir veya daha fazla [runtıme_ınfo_flags](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) sabit listesi değerleri.  
  
 `pDirectory`  
 [out] Çalışma zamanı başarıyla tamamlandıktan sonra dizin yolu içeren arabellek.  
  
 `dwDirectory`  
 [in] Dizin arabelleği uzunluğu.  
  
 `dwDirectoryLength`  
 [out] Dizin yolu dizenin uzunluğu bir işaretçi.  
  
 `pVersion`  
 [out] Çalışma zamanı başarıyla tamamlandığında uygulamanın sürüm sayısını içeren bir arabelleği.  
  
 `cchBuffer`  
 [in] Sürüm dizesi arabelleği uzunluğu.  
  
 `dwlength`  
 [out] Sürüm dizesinin uzunluğunu işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|ERROR_INSUFFICIENT_BUFFER|Dizin arabelleği dizin yolu depolamak için yeterli büyüklükte değil.<br /><br /> - veya -<br /><br /> Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRequestedRuntimeInfo` Yöntemi mutlaka en son sürümü bilgisayarda yüklü değil işlem yüklenen sürümü çalışma zamanı bilgilerini döndürür.  
  
 .NET Framework sürüm 2. 0'da, en son yüklenen sürüm bilgilerini kullanarak alabilirsiniz `GetRequestedRuntimeInfo` yöntemini aşağıdaki şekilde:  
  
-   Belirtin `pExe`, `pwszVersion`, ve `pConfigurationFile` parametreleri null olarak.  
  
-   RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin `RUNTIME_INFO_FLAGS` sabit listeleri için `runtimeInfoFlags` parametresi.  
  
 `GetRequestedRuntimeInfo` Yöntemi en son CLR sürümünü aşağıdaki durumlarda döndürmüyor:  
  
-   Belirli bir CLR sürümü belirten bir uygulama yapılandırma dosyası yok. İçin null belirtin bile .NET Framework yapılandırma dosyası kullanacağını Not `pConfigurationFile` parametresi.  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önceki bir CLR sürümünü belirtme yöntemi çağrıldı.  
  
-   Önceki bir CLR sürümü için derlenmiş bir uygulama şu anda çalışıyor.  
  
 İçin `runtimeInfoFlags` parametresini belirtebilirsiniz mimarisi sabitlerini yalnızca biri `RUNTIME_INFO_FLAGS` birer birer sabit listesi:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

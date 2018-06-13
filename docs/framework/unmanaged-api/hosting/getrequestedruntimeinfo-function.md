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
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434987"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo İşlevi
Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürümü ve dizin bilgilerini alır.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pExe`  
 [in] Uygulamanın adı.  
  
 `pwszVersion`  
 [in] Çalışma zamanı sürüm sayısını belirten bir dize.  
  
 `pConfigurationFile`  
 [in] İle ilişkili yapılandırma dosyasının adını `pExe`.  
  
 `startupFlags`  
 [in] Bir veya daha fazlasının [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırma değerleri.  
  
 `runtimeInfoFlags`  
 [in] Bir veya daha fazlasının [runtıme_ınfo_flags](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) numaralandırma değerleri.  
  
 `pDirectory`  
 [out] Çalışma zamanı başarıyla tamamlandıktan sonra dizin yolunu içeren bir arabellek.  
  
 `dwDirectory`  
 [in] Dizin arabellek uzunluğu.  
  
 `dwDirectoryLength`  
 [out] Dizin yolu dizesi uzunluğu için bir işaretçi.  
  
 `pVersion`  
 [out] İşlem başarıyla tamamlandıktan sonra çalışma zamanının sürüm numarasını içerir arabelleği.  
  
 `cchBuffer`  
 [in] Sürüm dizesi arabellek uzunluğu.  
  
 `dwlength`  
 [out] Sürüm dizesi uzunluğu için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|ERROR_INSUFFICIENT_BUFFER|Dizin arabelleği dizin yolu depolamak için yeterli büyüklükte değil.<br /><br /> - veya -<br /><br /> Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRequestedRuntimeInfo` Yöntemi mutlaka en son sürümü bilgisayarda yüklü değil işlemine yüklenen sürümüyle ilgili çalışma zamanı bilgilerini döndürür.  
  
 .NET Framework sürüm 2. 0'da, kullanarak en son yüklenen sürümü hakkında bilgi alabilirsiniz `GetRequestedRuntimeInfo` yöntemini aşağıdaki şekilde:  
  
-   Belirtin `pExe`, `pwszVersion`, ve `pConfigurationFile` parametre null olarak.  
  
-   RUNTIME_INFO_UPGRADE_VERSION bayrağı belirtin `RUNTIME_INFO_FLAGS` sabit listeleri için `runtimeInfoFlags` parametresi.  
  
 `GetRequestedRuntimeInfo` Yöntemi, aşağıdaki durumlarda en son CLR sürümü dönmez:  
  
-   Belirli bir CLR sürümü belirten bir uygulama yapılandırma dosyası yok. .NET Framework için null belirtin olsa bile yapılandırma dosyasını kullanacak Not `pConfigurationFile` parametresi.  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi, daha önce bir CLR sürüm belirtme çağrıldı.  
  
-   Önceki bir CLR sürümü için derlenmiş bir uygulama şu anda çalışıyor.  
  
 İçin `runtimeInfoFlags` parametresi, yalnızca birini belirtebilir mimarisi sabitleri `RUNTIME_INFO_FLAGS` sabit bir zaman:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

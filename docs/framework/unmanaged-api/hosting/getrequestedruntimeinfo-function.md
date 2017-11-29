---
title: "GetRequestedRuntimeInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeInfo
helpviewer_keywords: GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cca74a1ff66392608802eacedcd74bb673919e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetRequestedRuntimeVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess işlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

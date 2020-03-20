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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178149"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo İşlevi
Bir uygulama tarafından istenen ortak dil çalışma süresi (CLR) hakkında sürüm ve dizin bilgileri alır.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 [içinde] Uygulamanın adı.  
  
 `pwszVersion`  
 [içinde] Çalışma zamanının sürüm numarasını belirten bir dize.  
  
 `pConfigurationFile`  
 [içinde] `pExe`' ile ilişkili yapılandırma dosyasının adı  
  
 `startupFlags`  
 [içinde] numaralandırma değerlerinden biri veya birkaçı [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
  
 `runtimeInfoFlags`  
 [içinde] [Numaralandırma değerlerinden](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) biri veya birkaçı RUNTIME_INFO_FLAGS.  
  
 `pDirectory`  
 [çıkış] Başarılı bir şekilde tamamlandığında çalışma zamanına giden dizin yolunu içeren bir arabellek.  
  
 `dwDirectory`  
 [içinde] Dizin arabelleği uzunluğu.  
  
 `dwDirectoryLength`  
 [çıkış] Dizin yolu dizesinin uzunluğuna işaretçi.  
  
 `pVersion`  
 [çıkış] Başarılı bir şekilde tamamlandığında çalışma zamanının sürüm numarasını içeren bir arabellek.  
  
 `cchBuffer`  
 [içinde] Sürüm dize arabelleği uzunluğu.  
  
 `dwlength`  
 [çıkış] Sürüm dizesinin uzunluğuna işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|ERROR_INSUFFICIENT_BUFFER|Dizin arabelleği dizin yolunu depolamak için yeterince büyük değil.<br /><br /> - veya -<br /><br /> Sürüm arabelleği sürüm dizesini depolamak için yeterince büyük değildir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem, `GetRequestedRuntimeInfo` işleme yüklenen sürüm le ilgili çalışma zamanı bilgilerini döndürür ve bu da bilgisayarda yüklü olan en son sürüm değildir.  
  
 .NET Framework sürüm 2.0'da, `GetRequestedRuntimeInfo` yöntemi aşağıdaki şekilde kullanarak en son yüklenen sürüm hakkında bilgi alabilirsiniz:  
  
- , `pExe` `pwszVersion`ve `pConfigurationFile` parametreleri null olarak belirtin.  
  
- Parametre için sayısallaştırmalarda `RUNTIME_INFO_FLAGS` RUNTIME_INFO_UPGRADE_VERSION bayrağı `runtimeInfoFlags` belirtin.  
  
 Yöntem, `GetRequestedRuntimeInfo` aşağıdaki durumlarda en son CLR sürümünü döndürmez:  
  
- Belirli bir CLR sürümünün yüklendiğini belirten bir uygulama yapılandırma dosyası vardır. .NET Framework'ün, parametre için null belirtseniz `pConfigurationFile` bile yapılandırma dosyasını kullanacağını unutmayın.  
  
- [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi daha önceki bir CLR sürümünü belirterek çağrıldı.  
  
- Önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.  
  
 Parametre `runtimeInfoFlags` için, numaralandırmanın `RUNTIME_INFO_FLAGS` mimari sabitlerinden yalnızca birini bir defada belirtebilirsiniz:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

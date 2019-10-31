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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136317"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo İşlevi
Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) hakkındaki sürüm ve dizin bilgilerini alır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
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
 'ndaki Uygulamanın adı.  
  
 `pwszVersion`  
 'ndaki Çalışma zamanının sürüm numarasını belirten bir dize.  
  
 `pConfigurationFile`  
 'ndaki `pExe`ilişkili yapılandırma dosyasının adı.  
  
 `startupFlags`  
 'ndaki Bir veya daha fazla [startup_flags](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırma değeri.  
  
 `runtimeInfoFlags`  
 'ndaki Bir veya daha fazla [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) numaralandırma değeri.  
  
 `pDirectory`  
 dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanına ait dizin yolunu içeren bir arabellek.  
  
 `dwDirectory`  
 'ndaki Dizin arabelleğinin uzunluğu.  
  
 `dwDirectoryLength`  
 dışı Dizin yolu dizesinin uzunluğuna yönelik bir işaretçi.  
  
 `pVersion`  
 dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanının sürüm numarasını içeren bir arabellek.  
  
 `cchBuffer`  
 'ndaki Sürüm dizesi arabelleğinin uzunluğu.  
  
 `dwlength`  
 dışı Sürüm dizesinin uzunluğuna yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|ERROR_INSUFFICIENT_BUFFER|Dizin arabelleği, dizin yolunu depolamaya yetecek kadar büyük değil.<br /><br /> veya<br /><br /> Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRequestedRuntimeInfo` yöntemi, işleme yüklenen sürüm hakkında, bilgisayarda yüklü en son sürüm olması gereken çalışma zamanı bilgilerini döndürür.  
  
 .NET Framework sürüm 2,0 ' de, aşağıdaki gibi `GetRequestedRuntimeInfo` metodunu kullanarak en son yüklenen sürüm hakkında bilgi edinebilirsiniz:  
  
- `pExe`, `pwszVersion`ve `pConfigurationFile` parametrelerini null olarak belirtin.  
  
- `runtimeInfoFlags` parametresi için `RUNTIME_INFO_FLAGS` numaralandırmalar içinde RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin.  
  
 `GetRequestedRuntimeInfo` yöntemi, aşağıdaki durumlarda en son CLR sürümünü döndürmez:  
  
- Belirli bir CLR sürümünü yüklemeyi belirten bir uygulama yapılandırma dosyası var. `pConfigurationFile` parametresi için null belirtseniz bile .NET Framework yapılandırma dosyasını kullanacaktır.  
  
- [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi, ÖNCEKI bir clr sürümü belirtilerek çağrıldı.  
  
- Daha önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.  
  
 `runtimeInfoFlags` parametresi için aynı anda `RUNTIME_INFO_FLAGS` numaralandırmanın mimari sabitlerinden yalnızca birini belirtebilirsiniz:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

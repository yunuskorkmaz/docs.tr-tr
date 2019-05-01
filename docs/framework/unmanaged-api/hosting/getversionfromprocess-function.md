---
title: GetVersionFromProcess İşlevi
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 452104939acf5de7bb151cba00d65fb6631c98d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985640"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess İşlevi
Belirtilen işlem tanımlayıcısıyla ilişkili olan ortak dil çalışma zamanı (CLR) sürüm numarasını alır.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hProcess`  
 [in] Bir işlem için bir tanıtıcı.  
  
 `pVersion`  
 [out] Yöntemi başarıyla tamamlanmasından sonra sürüm numarası dizesi içeren bir arabelleği.  
  
 `cchBuffer`  
 [in] Sürüm arabellek uzunluğu.  
  
 `pdwLength`  
 [out] Sürüm numarası dizenin uzunluğu bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`pVersion` NULL ve `cchBuffer` null değil veya bunun tersi de geçerlidir.<br /><br /> -veya-<br /><br /> `hProcess` bir işlem için geçerli bir tanıtıcı değil.<br /><br /> -veya-<br /><br /> CLR yüklü değil.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` null veya sürüm dizesinin uzunluğunu değerinden küçük değil.|  
|E_NOTIMPL|Bu yöntem, Microsoft Windows 95, Windows 98 Microsoft veya Microsoft Windows Millennium Edition işletim sisteminde kullanılabilir değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeInfo İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

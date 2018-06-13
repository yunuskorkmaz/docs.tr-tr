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
ms.openlocfilehash: 0b57d04a8a49371872c679a331b5ae9c45dce797
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433079"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess İşlevi
Belirtilen işlem tanıtıcı ile ilişkili ortak dil çalışma zamanı (CLR) sürüm numarasını alır.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hProcess`  
 [in] Bir işlem için bir tanıtıcı.  
  
 `pVersion`  
 [out] Yöntem başarılı tamamlanmasından sonra sürüm numarası dizesi içeren bir arabellek.  
  
 `cchBuffer`  
 [in] Sürüm arabellek uzunluğu.  
  
 `pdwLength`  
 [out] Sürüm numarası dize uzunluğu için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`pVersion` NULL ve `cchBuffer` null değil veya tam tersi.<br /><br /> -veya-<br /><br /> `hProcess` bir işlem için geçerli bir tanıtıcı değil.<br /><br /> -veya-<br /><br /> CLR yüklü değil.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` null veya sürüm dizesi uzunluğundan daha az olabilir.|  
|E_NOTIMPL|Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılabilir değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetRequestedRuntimeInfo İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

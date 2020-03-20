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
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178123"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess İşlevi
Belirtilen işlem tanıtıcısıyla ilişkili ortak dil çalışma zamanının (CLR) sürüm numarasını alır.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hProcess`  
 [içinde] Bir işlemin sapı.  
  
 `pVersion`  
 [çıkış] Yöntemin başarıyla tamamlanmasından sonra sürüm numarası dizesini içeren bir arabellek.  
  
 `cchBuffer`  
 [içinde] Sürüm arabelleği uzunluğu.  
  
 `pdwLength`  
 [çıkış] Sürüm numarası dizesinin uzunluğuna işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_ınvalıdarg|`pVersion`null ve `cchBuffer` null değildir, ya da tersi.<br /><br /> -veya-<br /><br /> `hProcess`bir işlem için geçerli bir tutamaç değildir.<br /><br /> -veya-<br /><br /> CLR dolu değil.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`null veya sürüm dize uzunluğu daha azdır.|  
|E_notımpl|Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılamaz.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeInfo İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

---
description: ': GetVersionFromProcess Işlevi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ab665d2984f79baf049009690b36782528094937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785256"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess İşlevi

Belirtilen işlem tanıtıcısıyla ilişkili ortak dil çalışma zamanının (CLR) sürüm numarasını alır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
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
 'ndaki Bir işleme yönelik bir tanıtıcı.  
  
 `pVersion`  
 dışı Yöntemi başarıyla tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.  
  
 `cchBuffer`  
 'ndaki Sürüm arabelleğinin uzunluğu.  
  
 `pdwLength`  
 dışı Sürüm numarası dizesinin uzunluğuna yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`pVersion` null ve `cchBuffer` null ya da tam tersi.<br /><br /> -veya-<br /><br /> `hProcess` bir işleme geçerli bir tanıtıcı değil.<br /><br /> -veya-<br /><br /> CLR yüklü değil.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` null veya sürüm dizesinin uzunluğundan daha küçük.|  
|E_NOTIMPL|Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılamaz.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetRequestedRuntimeInfo İşlevi](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion İşlevi](getrequestedruntimeversion-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)

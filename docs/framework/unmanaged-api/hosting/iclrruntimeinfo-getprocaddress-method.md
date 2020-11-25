---
title: ICLRRuntimeInfo::GetProcAddress Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 028cfd51a713d8598598566a5b1edcf3fc70ecfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732066"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a>ICLRRuntimeInfo::GetProcAddress Metodu

Bu arabirimle ilişkili ortak dil çalışma zamanından (CLR) aktarılmış olan belirli bir işlevin adresini alır.  
  
 Bu yöntem [GetRealProcAddress](getrealprocaddress-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszProcName`  
 'ndaki İçe aktarılmış işlevin adı.  
  
 `ppProc`  
 dışı İçe aktarılmış işlevin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pszProcName` ya da `ppProc` null.|  
|CLR_E_SHIM_RUNTIMEEXPORT|Belirtilen işlev, dışarıya aktarılmış bir işlev değil.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)

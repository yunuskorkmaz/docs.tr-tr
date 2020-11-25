---
title: ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: 8020db491c3b66be38a9f6cbcb7551721859dcd5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723122"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi

Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar. Bu yöntem `startupFlags` , [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevlerinde parametresinin kullanımını yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwStartupFlags`  
 'ndaki Ayarlanacak konak başlangıç bayrakları. [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.  
  
 `pwzHostConfigFile`  
 'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir. Aksi takdirde, A iş parçacığı b iş parçacığını `SetStartupFlags` başlattıktan önce ve ' a çağrı tamamladıktan sonra yöntemini çağırabilir `SetStartupFlags` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)

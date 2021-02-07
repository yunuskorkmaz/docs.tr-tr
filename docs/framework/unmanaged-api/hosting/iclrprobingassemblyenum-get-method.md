---
description: ': ICLRProbingAssemblyEnum:: get yöntemi hakkında daha fazla bilgi edinin'
title: ICLRProbingAssemblyEnum::Get Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 77fb93b30a3b9b01b32fef9af661c84f484ef758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716529"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get Yöntemi

Belirtilen dizinde derleme kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwIndex`  
 'ndaki Döndürülecek derleme kimliğinin sıfır tabanlı dizini.  
  
 `pwzBuffer`  
 dışı Bütünleştirilmiş kod kimlik verilerini içeren bir arabellek.  
  
 `pcchBufferSize`  
 [in, out] `pwzBuffer` Arabelleğin boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Get` başarıyla döndürüldü.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` çok küçük.|  
|ERROR_NO_MORE_ITEMS|Sabit listesi daha fazla öğe içermiyor.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 0 dizinindeki kimlik, işlemci mimarisine özgü kimliktir. Dizin 1 ' deki kimlik, Microsoft ara dili (MSIL) için mimari olarak nötr derlemedir. Dizin 2 ' deki kimlik hiçbir mimari bilgisi içermiyor.  
  
 `Get` genellikle iki kez çağırılır. İlk çağrı için null bir değer sağlar `pwzBuffer` ve `pcchBufferSize` için uygun boyuta ayarlanır `pwzBuffer` . İkinci çağrı uygun boyutta bir boyut sağlar `pwzBuffer` ve tamamlandıktan sonra kurallı derleme kimliği verilerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRProbingAssemblyEnum Arabirimi](iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)

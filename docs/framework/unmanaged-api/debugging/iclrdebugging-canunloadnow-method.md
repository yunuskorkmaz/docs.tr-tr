---
title: ICLRDebugging::CanUnloadNow Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: e89d936c528ea7482487a8629dbd882f6f67483e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723577"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow Yöntemi

Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>Parametreler  

 `hmodule`  
 'ndaki Hedef işlemdeki bir modülün temel adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Tarafından başvurulan modül `hmodule` bellekten kaldırılabilir.|  
|S_FALSE|Tarafından başvurulan modül `hmodule` hala kullanımda.|  
|COR_E_NOT_CLR|Belirtilen modül bir CLR modülü değil.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, tüm `ICorDebug*` arabirimlerin örneklerinin serbest bırakıldığını ve şu anda [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) metoduna yapılan bir çağrı içinde iş parçacığı olup olmadığını denetler.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

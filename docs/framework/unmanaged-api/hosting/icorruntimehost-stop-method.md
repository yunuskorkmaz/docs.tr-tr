---
title: ICorRuntimeHost::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: 5fcf8bc861b2ef0b8ea9f5a5e46585564cc26615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127696"
---
# <a name="icorruntimehoststop-method"></a>ICorRuntimeHost::Stop Yöntemi
Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlem tamamlanamadı.|  
|E_FAıL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz. Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Stop` yöntemi çağırmak genellikle gereksizdir, çünkü işlem çıkış sırasında kod yürütmeyi durduruyor.  
  
> [!NOTE]
> `Stop`çağrısından sonra, CLR aynı işleme yeniden başlatılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

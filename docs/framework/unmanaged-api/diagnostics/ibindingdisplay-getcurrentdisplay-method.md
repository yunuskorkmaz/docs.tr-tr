---
title: IBindingDisplay::GetCurrentDisplay Yöntemi
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: d52f089923d16f93345444c07ff8e0619644f2eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725163"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay Yöntemi

Geçerli bağlama görüntüleme bilgilerini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `display`  
 [Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 [IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.  
  
 Çağıran, `SAFEARRAY` [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen belleği serbest bırakma olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** BindingDisplay. h  
  
 **Kitaplık:** BindingDisplay. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IBindingDisplay Arabirimi](ibindingdisplay-interface.md)
- [InitializeForProcess Yöntemi](ibindingdisplay-initializeforprocess-method.md)

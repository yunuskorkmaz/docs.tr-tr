---
title: IBindingDisplay::InitializeForProcess Yöntemi
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8954c2f6ecaf2767dd01b0601096d9e3f6df9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425460"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess Yöntemi
Başlatır [Ibindingdisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pid`  
 [in] İşlem tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı çağrıları `InitializeForProcess` yöntemi oluşturma zamanında bağlama görüntü başlatılamadı. `InitializeForProcess` önce başka bir yöntem oluşturma zamanında üzerinde çağrılmalıdır `IBindingDisplay` olarak adlandırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** BindingDisplay.h  
  
 **Kitaplığı:** BindingDisplay.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IBindingDisplay Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)

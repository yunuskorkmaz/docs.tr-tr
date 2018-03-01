---
title: "IBindingDisplay::InitializeForProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56f55788fcaf08507f413a03c5364ce3bcdbbf3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 Hata ayıklayıcı çağrıları `InitializeForProcess` yöntemi oluşturma zamanında bağlama görüntü başlatılamadı. `InitializeForProcess`önce başka bir yöntem oluşturma zamanında üzerinde çağrılmalıdır `IBindingDisplay` olarak adlandırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** BindingDisplay.h  
  
 **Kitaplığı:** BindingDisplay.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IBindingDisplay Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)

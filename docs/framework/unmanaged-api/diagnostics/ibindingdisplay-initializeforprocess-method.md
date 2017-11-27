---
title: "IBindingDisplay::InitializeForProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.InitializeForProcess
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e5ab3bb38d23e5841a347a348a09deb3b5639962
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Ibindingdisplay arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)

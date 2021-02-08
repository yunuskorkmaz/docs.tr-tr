---
description: ': IBindingDisplay:: InitializeForProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cf7f0f4d057659089bd7da173e5fac98a7c00dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800418"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess Yöntemi

[IBindingDisplay](ibindingdisplay-interface.md) nesnesini başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pid`  
 'ndaki İşlem tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, `InitializeForProcess` bağlama görüntüsünü başlatmak için oluşturma zamanında yöntemini çağırır. `InitializeForProcess` üzerinde diğer herhangi bir yöntem çağrılmadan önce oluşturulma zamanında çağrılmalıdır `IBindingDisplay` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** BindingDisplay. h  
  
 **Kitaplık:** BindingDisplay. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IBindingDisplay Arabirimi](ibindingdisplay-interface.md)

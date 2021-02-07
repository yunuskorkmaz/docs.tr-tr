---
description: ': ICorPublish:: GetProcess metodu hakkında daha fazla bilgi edinin'
title: ICorPublish::GetProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: d288a772274618cc99b63a68b37e84e543957b44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721989"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess Yöntemi

Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pid`  
 'ndaki İşlemin tanımlayıcısı.  
  
 `ppProcess`  
 dışı İşlemi temsil eden bir örneğin adresine yönelik bir işaretçi `ICorPublishProcess` .  
  
## <a name="remarks"></a>Açıklamalar  

 `GetProcess` işlem yoksa veya geçerli kullanıcı tarafından hata ayıklanabilecek yönetilen bir işlem değilse başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublish Arabirimi](icorpublish-interface.md)

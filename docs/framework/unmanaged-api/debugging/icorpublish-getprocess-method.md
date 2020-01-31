---
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
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790741"
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
 dışı İşlemi temsil eden bir `ICorPublishProcess` örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 işlem yoksa `GetProcess` başarısız olur veya geçerli kullanıcı tarafından hata ayıklanabilecek yönetilen bir işlem değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublish Arabirimi](icorpublish-interface.md)

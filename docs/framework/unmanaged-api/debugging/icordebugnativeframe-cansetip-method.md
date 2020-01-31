---
title: ICorDebugNativeFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792800"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP Yöntemi
Yerel koddaki belirtilen konum konumuna yönerge işaretçisini (IP) ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 'ndaki Yönerge işaretçisi için istenen ayar.  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` yöntemini kullanın. `CanSetIP` S_OK dışında herhangi bir HRESULT döndürürse `ICorDebugNativeFrame::SetIP`yine de çağırabilirsiniz, ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

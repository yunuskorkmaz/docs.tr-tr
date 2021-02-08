---
description: ': ICorDebugILFrame:: CanSetIP yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: d6ba0d073e8807ac6173f7f3e3982fe1d3eb4e01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791445"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP Yöntemi

Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `nOffset`  
 'ndaki Yönerge işaretçisi için istenen ayar.  
  
## <a name="remarks"></a>Açıklamalar  

 `CanSetIP` [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) metodunu çağırmadan önce yöntemini kullanın. `CanSetIP`S_OK dışında BIR HRESULT döndürürse, yine de çağırabilirsiniz `ICorDebugILFrame::SetIP` , ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug, h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

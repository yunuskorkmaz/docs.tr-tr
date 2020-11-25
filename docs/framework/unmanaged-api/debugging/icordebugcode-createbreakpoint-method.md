---
title: ICorDebugCode::CreateBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: ade428ce001a6b40e2fed67f4f23b12cef5ea30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717664"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint Yöntemi

Belirtilen uzaklığında Bu kod kesiminde bir kesme noktası oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `offset`  
 'ndaki Kesme noktasının oluşturulacağı konum.  
  
 `ppBreakpoint`  
 dışı Kesme noktasını temsil eden bir "ICorDebugFunctionBreakpoint" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Kesme noktası etkin olmadan önce, işlem nesnesine eklenmelidir.  
  
 Bu kod Microsoft ara dili (MSIL) kodlarsa ve kodun tam zamanında (JıT) derlenmiş bir sürümü varsa, kesme noktası JıT ile derlenen kodda da uygulanır. (Kod JıT olarak derlenmişse, aynı değer de geçerlidir.)  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

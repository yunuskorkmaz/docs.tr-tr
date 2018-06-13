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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399128"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint Yöntemi
Bu kod kesimi belirtilen uzaklığında bir kesme noktası oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `offset`  
 [in] Uzaklığı kesme noktası oluşturmak.  
  
 `ppBreakpoint`  
 [out] Kesme noktası temsil eden bir "ICorDebugFunctionBreakpoint" nesnesinin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kesme noktası etkinleştirilmeden önce işlem nesnesine eklenmelidir.  
  
 Bu kodu Microsoft Ara dili (MSIL) koddur ve bir tam zamanında (JIT) yoktur-kesme kodunun derlenmiş, yerel sürümünü JIT derlenmiş kod da uygulanır. (Aynı kodu daha sonra JIT derlenmiş ise geçerlidir.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 

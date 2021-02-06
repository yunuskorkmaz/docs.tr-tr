---
description: ': ICorDebugILFrame:: GetArgument Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::GetArgument Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: c845f3c07502f3b1ce564833ee6ef98e3305463f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650527"
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument Metodu

Bu Microsoft ara dili (MSIL) yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwIndex`  
 'ndaki Bu MSIL yığın çerçevesindeki bağımsız değişkenin dizini.  
  
 `ppValue`  
 dışı Alınan değeri temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetArgument`Yöntemi, BIR MSIL yığın çerçevesinde veya tam zamanında (JIT) derlenmiş bir çerçevede kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

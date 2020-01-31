---
title: ICorDebugFunction::GetCurrentVersionNumber Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 5e080e9aa89816b24aa2eb1b6b1be823922e86fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794514"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber Metodu
Bu ICorDebugFunction nesnesi tarafından temsil edilen işlevde yapılan en son düzenlemenin sürüm numarasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnCurrentVersion`  
 dışı Bu işlevde yapılan en son düzenlemenin sürüm numarası olan bir tamsayı değerine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlevde yapılan en son düzenlemenin sürüm numarası, işlevin sürüm numarasından daha büyük olabilir. İşlevin sürüm numarasını almak için [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) yöntemini veya [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

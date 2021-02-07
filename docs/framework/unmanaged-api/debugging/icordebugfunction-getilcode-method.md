---
description: ': ICorDebugFunction:: GetILCode yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFunction::GetILCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 3b7bb29a028b189b24d3fbf02edc8190d9989a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692530"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode Metodu

Bu ICorDebugFunction nesnesiyle ilişkili Microsoft ara dili (MSIL) kodunu temsil eden ICorDebugCode örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppCode`  
 dışı `ICorDebugCode` Işlev MSIL 'e derlenmediği takdirde, örneğin işaretçisi veya null.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu işlevde Düzenle ve devam et izni verildiyse, `GetILCode` yöntemi, ortak dil çalışma zamanında (CLR) bu işlevin düzenlenmiş sürümüne karşılık gelen MSIL kodunu alır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

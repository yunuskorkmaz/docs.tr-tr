---
description: ': ICorDebugCode:: GetEnCRemapSequencePoints metodu hakkında daha fazla bilgi edinin'
title: ICorDebugCode::GetEnCRemapSequencePoints Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetEnCRemapSequencePoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetEnCRemapSequencePoints
helpviewer_keywords:
- GetEnCRemapSequencePoints method [.NET Framework debugging]
- ICorDebugCode::GetEnCRemapSequencePoints method [.NET Framework debugging]
ms.assetid: 8463a98a-de4a-418e-beb0-9611885ae6b0
topic_type:
- apiref
ms.openlocfilehash: e9785460490aa602a49dff3ab972b409dde48cdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711173"
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a>ICorDebugCode::GetEnCRemapSequencePoints Yöntemi

Bu yöntem .NET Framework geçerli sürümünde uygulanmıyor.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEnCRemapSequencePoints(
    [in] ULONG32 cMap,
    [out] ULONG32 *pcMap,
    [out, size_is(cMap), length_is(*pcMap)]
        ULONG32 offsets[]
);
```

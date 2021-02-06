---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess2:: GetVersion yöntemi'
title: ICorDebugProcess2::GetVersion Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 8472e811ea4df1f99fb4e27b55f3561fae0c8a21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650111"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion Yöntemi

Bu işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Parametreler

`version`\
dışı Çalışma zamanının sürüm numarasını depolayan COR_VERSION yapısına yönelik bir işaretçi.

## <a name="remarks"></a>Açıklamalar

`GetVersion`İşlem, işleme hiçbir çalışma zamanı yüklenmemiş ise, yöntem bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

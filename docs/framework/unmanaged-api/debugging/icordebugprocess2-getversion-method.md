---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f3be81431201a4bb6011ea9b8f973061d3d101
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948882"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion Yöntemi

Bu işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Parametreler

`version`\
[out] Çalışma zamanı sürüm numarasını depolayan bir cor_versıon yapısı işaretçisi.

## <a name="remarks"></a>Açıklamalar

`GetVersion` Yöntemi, hiçbir çalışma zamanı işleminde yüklerse bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug.idl, CorDebug.h

**Kitaplığı:** CorGuids.lib

**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

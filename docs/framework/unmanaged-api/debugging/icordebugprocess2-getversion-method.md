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
ms.openlocfilehash: 391b848d3b3f66f6af6bf3adbefb6e94d526e748
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213510"
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

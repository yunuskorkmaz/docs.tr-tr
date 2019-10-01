---
title: ICorDebugCode2::GetCodeChunks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700724"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks Yöntemi

Bu kod nesnesinin oluştuğu kod öbeklerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>Parametreler

 `cbufSize`  
 'ndaki @No__t-0 dizisinin boyutu.

 `pcnumChunks`  
 dışı @No__t-0 dizisinde döndürülen öbeklerin sayısı.

 `chunks`  
 dışı Her biri tek bir kod öbeğini temsil eden bir "CodeChunkInfo" yapıları dizisi. @No__t-0 değeri 0 ise, bu parametre null olabilir.

## <a name="remarks"></a>Açıklamalar

 Kod öbekleri hiçbir şekilde çakışacaktır ve [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md)tarafından bitiştirildiği sırayı takip eder. .NET Framework sürüm 2,0 ' deki bir Microsoft ara dili (MSIL) kod nesnesi, tek bir kod öbeğini kapsar.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** CorDebug. IDL, CorDebug. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 

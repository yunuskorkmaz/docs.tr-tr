---
description: 'Daha fazla bilgi edinin: ICorDebugCode2:: GetCompilerFlags yöntemi'
title: ICorDebugCode2::GetCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: 820b6d2392b2b91bbfc8a85b165c4d73a2546859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711130"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="b53e5-103">ICorDebugCode2::GetCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="b53e5-103">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="b53e5-104">Bu kod nesnesinin, yerel görüntü Oluşturucu (Ngen.exe) kullanılarak derlenen ya da oluşturulan ya da oluşturulduğu koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="b53e5-104">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="b53e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b53e5-105">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="b53e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b53e5-106">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="b53e5-107">dışı JıT derleyicisinin veya yerel görüntü oluşturucunun davranışını belirten [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b53e5-107">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="b53e5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b53e5-108">Requirements</span></span>

<span data-ttu-id="b53e5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53e5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b53e5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b53e5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b53e5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b53e5-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b53e5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53e5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

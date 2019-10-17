---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebed8ea1d4943007f8f18b0baa1c676a78207c2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395500"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="1ea3e-102">ICorDebugCode2::GetCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="1ea3e-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="1ea3e-103">Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="1ea3e-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="1ea3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ea3e-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="1ea3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ea3e-105">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="1ea3e-106">dışı JıT derleyicisinin veya yerel görüntü oluşturucunun davranışını belirten [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ea3e-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ea3e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ea3e-107">Requirements</span></span>

<span data-ttu-id="1ea3e-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea3e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1ea3e-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ea3e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="1ea3e-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ea3e-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1ea3e-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea3e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

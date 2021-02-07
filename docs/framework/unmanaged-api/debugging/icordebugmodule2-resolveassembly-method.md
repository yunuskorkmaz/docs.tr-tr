---
description: 'Daha fazla bilgi edinin: ICorDebugModule2:: ResolveAssembly Yöntemi'
title: ICorDebugModule2::ResolveAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: fba53b8ff76e4d3deb1876d2a20a7a2edc20bd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722600"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="40124-103">ICorDebugModule2::ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40124-103">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="40124-104">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="40124-104">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="40124-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40124-105">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="40124-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40124-106">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="40124-107">'ndaki `mdToken` Derlemeye başvuran bir değer.</span><span class="sxs-lookup"><span data-stu-id="40124-107">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="40124-108">dışı Derlemeyi temsil eden ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40124-108">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="40124-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40124-109">Remarks</span></span>

<span data-ttu-id="40124-110">, Çağrıldığında derleme zaten yüklü değilse `ResolveAssembly` , CORDBG_E_CANNOT_RESOLVE_ASSEMBLY HRESULT değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="40124-110">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="40124-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40124-111">Requirements</span></span>

<span data-ttu-id="40124-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40124-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="40124-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40124-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="40124-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40124-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="40124-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40124-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

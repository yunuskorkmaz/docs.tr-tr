---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359698"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="ee563-102">ICorDebugModule2::ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee563-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="ee563-103">Belirtilen meta veri belirteci tarafından başvurulan derlemenin çözümler.</span><span class="sxs-lookup"><span data-stu-id="ee563-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee563-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee563-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="ee563-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee563-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="ee563-106">[in] Bir `mdToken` derlemesine başvuran bir değer.</span><span class="sxs-lookup"><span data-stu-id="ee563-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="ee563-107">[out] Bir işaretçi adresine Icordebugassembly nesnenin bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee563-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee563-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee563-108">Remarks</span></span>

<span data-ttu-id="ee563-109">Derleme zaten ne zaman yüklenmezse `ResolveAssembly` çağrıldığında bir HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ee563-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee563-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee563-110">Requirements</span></span>

<span data-ttu-id="ee563-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee563-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ee563-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee563-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ee563-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee563-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ee563-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee563-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

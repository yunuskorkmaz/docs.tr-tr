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
ms.openlocfilehash: 5f618f6779f6931785bba18f70fb1ac9baf46753
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137185"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="5dca8-102">ICorDebugProcess2::GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5dca8-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="5dca8-103">Bu işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="5dca8-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5dca8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dca8-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="5dca8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5dca8-105">Parameters</span></span>

`version`\
<span data-ttu-id="5dca8-106">dışı Çalışma zamanının sürüm numarasını depolayan bir COR_VERSION yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5dca8-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dca8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5dca8-107">Remarks</span></span>

<span data-ttu-id="5dca8-108">`GetVersion` yöntemi, işleme hiçbir çalışma zamanı yüklenmediyse bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5dca8-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="5dca8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5dca8-109">Requirements</span></span>

<span data-ttu-id="5dca8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dca8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5dca8-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5dca8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5dca8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5dca8-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5dca8-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dca8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

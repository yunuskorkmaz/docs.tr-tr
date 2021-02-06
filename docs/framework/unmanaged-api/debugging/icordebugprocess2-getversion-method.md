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
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="da776-103">ICorDebugProcess2::GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da776-103">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="da776-104">Bu işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="da776-104">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="da776-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da776-105">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="da776-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da776-106">Parameters</span></span>

`version`\
<span data-ttu-id="da776-107">dışı Çalışma zamanının sürüm numarasını depolayan COR_VERSION yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="da776-107">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="da776-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da776-108">Remarks</span></span>

<span data-ttu-id="da776-109">`GetVersion`İşlem, işleme hiçbir çalışma zamanı yüklenmemiş ise, yöntem bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="da776-109">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="da776-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da776-110">Requirements</span></span>

<span data-ttu-id="da776-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da776-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="da776-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da776-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="da776-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="da776-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="da776-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da776-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

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
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="d155c-102">ICorDebugProcess2::GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d155c-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="d155c-103">Bu işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="d155c-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="d155c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d155c-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="d155c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d155c-105">Parameters</span></span>

`version`\
<span data-ttu-id="d155c-106">dışı Çalışma zamanının sürüm numarasını depolayan COR_VERSION yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d155c-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="d155c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d155c-107">Remarks</span></span>

<span data-ttu-id="d155c-108">`GetVersion`İşlem, işleme hiçbir çalışma zamanı yüklenmemiş ise, yöntem bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d155c-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="d155c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d155c-109">Requirements</span></span>

<span data-ttu-id="d155c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d155c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d155c-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d155c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="d155c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d155c-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d155c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d155c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

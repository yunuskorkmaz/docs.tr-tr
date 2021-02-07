---
description: ': ICorDebugCode2:: Getcodeöbekleri yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 371d077466ff2390293d9d4e320d4c95a992fe54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764976"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="adb1c-103">ICorDebugCode2::GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adb1c-103">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="adb1c-104">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="adb1c-104">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="adb1c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adb1c-105">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="adb1c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adb1c-106">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="adb1c-107">'ndaki `chunks` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="adb1c-107">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="adb1c-108">dışı Dizide döndürülen öbeklerin sayısı `chunks` .</span><span class="sxs-lookup"><span data-stu-id="adb1c-108">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="adb1c-109">dışı Her biri tek bir kod öbeğini temsil eden bir "CodeChunkInfo" yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="adb1c-109">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="adb1c-110">Değeri `cbufSize` 0 ise, bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="adb1c-110">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="adb1c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adb1c-111">Remarks</span></span>

<span data-ttu-id="adb1c-112">Kod öbekleri hiçbir şekilde çakışacaktır ve [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md)tarafından bitiştirildiği sırayı takip eder.</span><span class="sxs-lookup"><span data-stu-id="adb1c-112">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="adb1c-113">.NET Framework sürüm 2,0 ' deki bir Microsoft ara dili (MSIL) kod nesnesi, tek bir kod öbeğini kapsar.</span><span class="sxs-lookup"><span data-stu-id="adb1c-113">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="adb1c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adb1c-114">Requirements</span></span>

<span data-ttu-id="adb1c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adb1c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="adb1c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="adb1c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="adb1c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="adb1c-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="adb1c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adb1c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

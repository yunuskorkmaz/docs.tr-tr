---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: CallFunction yöntemi'
title: ICorDebugEval::CallFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: c0978ab3bdffc83e3eb5e3a6553e7f374ab6d5da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694194"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="3f800-103">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f800-103">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="3f800-104">Belirtilen işleve bir çağrı kurar.</span><span class="sxs-lookup"><span data-stu-id="3f800-104">Sets up a call to the specified function.</span></span>

<span data-ttu-id="3f800-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3f800-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3f800-106">Bunun yerine [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f800-106">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f800-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f800-107">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="3f800-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f800-108">Parameters</span></span>

`pFunction`\
<span data-ttu-id="3f800-109">'ndaki Çağrılacak işlevi belirten ICorDebugFunction nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f800-109">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="3f800-110">'ndaki İşlevin bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="3f800-110">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="3f800-111">'ndaki Her biri, işleve geçirilecek bir bağımsız değişken belirten ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f800-111">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f800-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f800-112">Remarks</span></span>

<span data-ttu-id="3f800-113">İşlev sanal ise, `CallFunction` sanal dağıtım yapar.</span><span class="sxs-lookup"><span data-stu-id="3f800-113">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="3f800-114">İşlev farklı bir uygulama etki alanında ise, tüm bağımsız değişkenler de bu uygulama etki alanında olduğu sürece bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="3f800-114">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f800-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f800-115">Requirements</span></span>

<span data-ttu-id="3f800-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f800-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3f800-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f800-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3f800-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f800-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3f800-119">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3f800-119">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="3f800-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f800-120">See also</span></span>

- [<span data-ttu-id="3f800-121">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f800-121">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)

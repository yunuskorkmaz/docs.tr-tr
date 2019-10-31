---
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
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085167"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="bf095-102">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf095-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="bf095-103">Belirtilen işleve bir çağrı kurar.</span><span class="sxs-lookup"><span data-stu-id="bf095-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="bf095-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bf095-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bf095-105">Bunun yerine [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf095-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf095-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf095-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="bf095-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf095-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="bf095-108">'ndaki Çağrılacak işlevi belirten ICorDebugFunction nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf095-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="bf095-109">'ndaki İşlevin bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="bf095-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="bf095-110">'ndaki Her biri, işleve geçirilecek bir bağımsız değişken belirten ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="bf095-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf095-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf095-111">Remarks</span></span>

<span data-ttu-id="bf095-112">İşlev sanal ise `CallFunction` sanal dağıtım yapar.</span><span class="sxs-lookup"><span data-stu-id="bf095-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="bf095-113">İşlev farklı bir uygulama etki alanında ise, tüm bağımsız değişkenler de bu uygulama etki alanında olduğu sürece bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="bf095-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf095-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf095-114">Requirements</span></span>

<span data-ttu-id="bf095-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf095-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bf095-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf095-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="bf095-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bf095-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bf095-118">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="bf095-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="bf095-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf095-119">See also</span></span>

- [<span data-ttu-id="bf095-120">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf095-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)

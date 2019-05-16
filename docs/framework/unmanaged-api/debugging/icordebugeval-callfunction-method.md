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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65225281fe3abaa20e69e96f4cd4d2a4b03a87ce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629935"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="0138f-102">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0138f-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="0138f-103">Belirtilen işlev çağrısı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0138f-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="0138f-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0138f-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0138f-105">Kullanım [Icordebugeval2::callparameterizedfunction](icordebugeval2-callparameterizedfunction-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="0138f-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="0138f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0138f-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="0138f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0138f-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="0138f-108">[in] İşaretçi ICorDebugFunction nesneye çağrılacak işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0138f-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="0138f-109">[in] İşlev için bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="0138f-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="0138f-110">[in] İşleve geçirilecek bağımsız değişken belirtir Icordebugvalue nesneyi işaret her biri bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0138f-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="0138f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0138f-111">Remarks</span></span>

<span data-ttu-id="0138f-112">Sanal bir işlev ise `CallFunction` sanal gönderim yapar.</span><span class="sxs-lookup"><span data-stu-id="0138f-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="0138f-113">İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de, uygulama etki alanında olduğu sürece, bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="0138f-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="0138f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0138f-114">Requirements</span></span>

<span data-ttu-id="0138f-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0138f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="0138f-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0138f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="0138f-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0138f-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0138f-118">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="0138f-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="0138f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0138f-119">See also</span></span>

- [<span data-ttu-id="0138f-120">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0138f-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)

---
description: ': Icordebugvariablehome:: Getargumentındex yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugvariablehome:: Getargumentındex yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 827ef55d3e3509cbfbfc8213ef5b53fbe2e2220e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690047"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="b34ce-103">Icordebugvariablehome:: Getargumentındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="b34ce-103">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="b34ce-104">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="b34ce-104">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="b34ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b34ce-105">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="b34ce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b34ce-106">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="b34ce-107">dışı Bağımsız değişken dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b34ce-107">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="b34ce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b34ce-108">Return Value</span></span>

<span data-ttu-id="b34ce-109">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34ce-109">The method returns the following values.</span></span>

|<span data-ttu-id="b34ce-110">Değer</span><span class="sxs-lookup"><span data-stu-id="b34ce-110">Value</span></span>|<span data-ttu-id="b34ce-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b34ce-111">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="b34ce-112">Yöntem çağrısı geçerli bir bağımsız değişken dizini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="b34ce-112">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="b34ce-113">Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b34ce-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b34ce-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b34ce-114">Remarks</span></span>

<span data-ttu-id="b34ce-115">Bağımsız değişken dizini bu bağımsız değişken için meta verileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b34ce-115">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="b34ce-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b34ce-116">Requirements</span></span>

<span data-ttu-id="b34ce-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b34ce-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b34ce-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b34ce-118">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b34ce-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b34ce-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b34ce-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b34ce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b34ce-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b34ce-121">See also</span></span>

- [<span data-ttu-id="b34ce-122">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b34ce-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

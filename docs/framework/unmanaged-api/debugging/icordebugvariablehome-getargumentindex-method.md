---
title: ICorDebugVariableHome::GetArgumentIndex yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986797"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="a2dd5-102">ICorDebugVariableHome::GetArgumentIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2dd5-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="a2dd5-103">İşlev bağımsız değişkeni dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2dd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2dd5-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="a2dd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2dd5-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="a2dd5-106">[out] Bağımsız değişken dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2dd5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2dd5-107">Return Value</span></span>

<span data-ttu-id="a2dd5-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-108">The method returns the following values.</span></span>

|<span data-ttu-id="a2dd5-109">Değer</span><span class="sxs-lookup"><span data-stu-id="a2dd5-109">Value</span></span>|<span data-ttu-id="a2dd5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2dd5-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="a2dd5-111">Yöntem çağrısının geçerli bağımsız değişken dizini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="a2dd5-112">Geçerli [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği yerel bir değişken temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2dd5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2dd5-113">Remarks</span></span>

<span data-ttu-id="a2dd5-114">Bağımsız değişken dizini, bu bağımsız değişken için meta verilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2dd5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2dd5-115">Requirements</span></span>

<span data-ttu-id="a2dd5-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2dd5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a2dd5-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2dd5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a2dd5-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2dd5-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a2dd5-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2dd5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a2dd5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2dd5-120">See also</span></span>

- [<span data-ttu-id="a2dd5-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2dd5-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

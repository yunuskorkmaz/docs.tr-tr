---
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
ms.openlocfilehash: 27a676fd1d2d7903943e44f8a7201b88af4fba89
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397001"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="cb618-102">Icordebugvariablehome:: Getargumentındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb618-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="cb618-103">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="cb618-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb618-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb618-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="cb618-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb618-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="cb618-106">dışı Bağımsız değişken dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb618-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb618-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb618-107">Return Value</span></span>

<span data-ttu-id="cb618-108">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb618-108">The method returns the following values.</span></span>

|<span data-ttu-id="cb618-109">Değer</span><span class="sxs-lookup"><span data-stu-id="cb618-109">Value</span></span>|<span data-ttu-id="cb618-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb618-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="cb618-111">Yöntem çağrısı geçerli bir bağımsız değişken dizini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="cb618-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="cb618-112">Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cb618-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb618-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb618-113">Remarks</span></span>

<span data-ttu-id="cb618-114">Bağımsız değişken dizini bu bağımsız değişken için meta verileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb618-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb618-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb618-115">Requirements</span></span>

<span data-ttu-id="cb618-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb618-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cb618-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb618-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="cb618-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb618-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cb618-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb618-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb618-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb618-120">See also</span></span>

- [<span data-ttu-id="cb618-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb618-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

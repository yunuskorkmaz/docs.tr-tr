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
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791044"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="9232c-102">Icordebugvariablehome:: Getargumentındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="9232c-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="9232c-103">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="9232c-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="9232c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9232c-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="9232c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9232c-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="9232c-106">dışı Bağımsız değişken dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9232c-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="9232c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9232c-107">Return Value</span></span>

<span data-ttu-id="9232c-108">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9232c-108">The method returns the following values.</span></span>

|<span data-ttu-id="9232c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="9232c-109">Value</span></span>|<span data-ttu-id="9232c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9232c-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="9232c-111">Yöntem çağrısı geçerli bir bağımsız değişken dizini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="9232c-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="9232c-112">Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9232c-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9232c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9232c-113">Remarks</span></span>

<span data-ttu-id="9232c-114">Bağımsız değişken dizini bu bağımsız değişken için meta verileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9232c-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="9232c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9232c-115">Requirements</span></span>

<span data-ttu-id="9232c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9232c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9232c-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9232c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="9232c-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9232c-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9232c-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9232c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9232c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9232c-120">See also</span></span>

- [<span data-ttu-id="9232c-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9232c-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

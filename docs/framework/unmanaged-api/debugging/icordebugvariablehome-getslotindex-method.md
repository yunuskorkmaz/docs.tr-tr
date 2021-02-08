---
description: ': Icordebugvariablehome:: Getslotındex yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugvariablehome:: Getslotındex yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 7f6ee01c2bfcee4c78f8463a7cefac1f90a3295f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790652"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="ef10d-103">Icordebugvariablehome:: Getslotındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef10d-103">ICorDebugVariableHome::GetSlotIndex Method</span></span>

<span data-ttu-id="ef10d-104">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="ef10d-104">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef10d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef10d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef10d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef10d-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="ef10d-107">dışı Yerel bir değişkenin yuva dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ef10d-107">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef10d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef10d-108">Return Value</span></span>  

 <span data-ttu-id="ef10d-109">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef10d-109">The method returns the following values.</span></span>  
  
|<span data-ttu-id="ef10d-110">Değer</span><span class="sxs-lookup"><span data-stu-id="ef10d-110">Value</span></span>|<span data-ttu-id="ef10d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef10d-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ef10d-112">Yöntem çağrısı ' de bir yuva dizini değeri döndürdü `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="ef10d-112">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ef10d-113">Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği bir işlev bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef10d-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef10d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef10d-114">Remarks</span></span>  

 <span data-ttu-id="ef10d-115">Bu yerel değişken için meta verileri almak için yuva dizini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef10d-115">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef10d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef10d-116">Requirements</span></span>  

 <span data-ttu-id="ef10d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef10d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef10d-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef10d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef10d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ef10d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef10d-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef10d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef10d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef10d-121">See also</span></span>

- [<span data-ttu-id="ef10d-122">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef10d-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

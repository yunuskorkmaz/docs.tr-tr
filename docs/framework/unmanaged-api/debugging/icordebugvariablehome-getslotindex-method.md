---
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
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396561"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="1d795-102">Icordebugvariablehome:: Getslotındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d795-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="1d795-103">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="1d795-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d795-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d795-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d795-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d795-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="1d795-106">dışı Yerel bir değişkenin yuva dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d795-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d795-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d795-107">Return Value</span></span>  
 <span data-ttu-id="1d795-108">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d795-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="1d795-109">Değer</span><span class="sxs-lookup"><span data-stu-id="1d795-109">Value</span></span>|<span data-ttu-id="1d795-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d795-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1d795-111">Yöntem çağrısı ' de bir yuva dizini değeri döndürdü `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="1d795-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1d795-112">Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği bir işlev bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d795-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d795-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d795-113">Remarks</span></span>  
 <span data-ttu-id="1d795-114">Bu yerel değişken için meta verileri almak için yuva dizini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d795-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d795-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d795-115">Requirements</span></span>  
 <span data-ttu-id="1d795-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d795-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d795-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d795-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d795-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d795-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d795-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d795-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d795-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d795-120">See also</span></span>

- [<span data-ttu-id="1d795-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d795-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

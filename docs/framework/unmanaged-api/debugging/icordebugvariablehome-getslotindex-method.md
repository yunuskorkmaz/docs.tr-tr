---
title: ICorDebugVariableHome::GetSlotIndex yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093760"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="1bd1c-102">ICorDebugVariableHome::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bd1c-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="1bd1c-103">Yerel değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd1c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bd1c-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd1c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bd1c-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="1bd1c-106">[out] Bir yerel değişken dizini yuva için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bd1c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1bd1c-107">Return Value</span></span>  
 <span data-ttu-id="1bd1c-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="1bd1c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="1bd1c-109">Value</span></span>|<span data-ttu-id="1bd1c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bd1c-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1bd1c-111">Bir yuva dizin değeri yöntem çağrısından döndürülen `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1bd1c-112">Geçerli [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği, işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd1c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bd1c-113">Remarks</span></span>  
 <span data-ttu-id="1bd1c-114">Yuva dizin, bu yerel değişken için meta verileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd1c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bd1c-115">Requirements</span></span>  
 <span data-ttu-id="1bd1c-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd1c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd1c-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bd1c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bd1c-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd1c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd1c-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd1c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd1c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-120">See also</span></span>

- [<span data-ttu-id="1bd1c-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bd1c-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

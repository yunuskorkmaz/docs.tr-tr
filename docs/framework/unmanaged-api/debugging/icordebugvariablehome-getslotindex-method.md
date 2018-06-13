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
ms.openlocfilehash: 61014e067b2afb8b7e4be0488ed6a3c7f1bd6fc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420706"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="72bfc-102">ICorDebugVariableHome::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="72bfc-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="72bfc-103">Yönetilen yuvası dizin yerel değişken alır.</span><span class="sxs-lookup"><span data-stu-id="72bfc-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72bfc-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72bfc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72bfc-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="72bfc-106">[out] Yerel değişken yuvası dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72bfc-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72bfc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72bfc-107">Return Value</span></span>  
 <span data-ttu-id="72bfc-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="72bfc-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="72bfc-109">Değer</span><span class="sxs-lookup"><span data-stu-id="72bfc-109">Value</span></span>|<span data-ttu-id="72bfc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72bfc-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="72bfc-111">Yöntem çağrısının yuvası dizin değeri döndürülen `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="72bfc-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="72bfc-112">Geçerli [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği bir işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72bfc-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72bfc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72bfc-113">Remarks</span></span>  
 <span data-ttu-id="72bfc-114">Yuva dizini, bu yerel değişken meta verilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72bfc-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72bfc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72bfc-115">Requirements</span></span>  
 <span data-ttu-id="72bfc-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72bfc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72bfc-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72bfc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72bfc-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72bfc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72bfc-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72bfc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bfc-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72bfc-120">See Also</span></span>  
 [<span data-ttu-id="72bfc-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72bfc-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

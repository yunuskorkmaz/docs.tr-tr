---
title: "ICorDebugVariableHome::GetSlotIndex yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3eb8ed980fd523d0b0d29fbef770652a1d96146f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="4e0f9-102">ICorDebugVariableHome::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e0f9-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="4e0f9-103">Yönetilen yuvası dizin yerel değişken alır.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e0f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e0f9-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e0f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e0f9-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="4e0f9-106">[out] Yerel değişken yuvası dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e0f9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e0f9-107">Return Value</span></span>  
 <span data-ttu-id="4e0f9-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="4e0f9-109">Değer</span><span class="sxs-lookup"><span data-stu-id="4e0f9-109">Value</span></span>|<span data-ttu-id="4e0f9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e0f9-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="4e0f9-111">Yöntem çağrısının yuvası dizin değeri döndürülen `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="4e0f9-112">Geçerli [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği bir işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e0f9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e0f9-113">Remarks</span></span>  
 <span data-ttu-id="4e0f9-114">Yuva dizini, bu yerel değişken meta verilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e0f9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e0f9-115">Requirements</span></span>  
 <span data-ttu-id="4e0f9-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e0f9-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e0f9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e0f9-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e0f9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e0f9-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0f9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-120">See Also</span></span>  
 [<span data-ttu-id="4e0f9-121">ICorDebugVariableHome arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e0f9-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

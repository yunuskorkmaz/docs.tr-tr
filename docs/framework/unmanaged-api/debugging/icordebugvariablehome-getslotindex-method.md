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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093760"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="eaed9-102">ICorDebugVariableHome::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaed9-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="eaed9-103">Yerel değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="eaed9-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaed9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaed9-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaed9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eaed9-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="eaed9-106">[out] Bir yerel değişken dizini yuva için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eaed9-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaed9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eaed9-107">Return Value</span></span>  
 <span data-ttu-id="eaed9-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="eaed9-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="eaed9-109">Değer</span><span class="sxs-lookup"><span data-stu-id="eaed9-109">Value</span></span>|<span data-ttu-id="eaed9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaed9-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="eaed9-111">Bir yuva dizin değeri yöntem çağrısından döndürülen `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="eaed9-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="eaed9-112">Geçerli [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği, işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eaed9-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaed9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaed9-113">Remarks</span></span>  
 <span data-ttu-id="eaed9-114">Yuva dizin, bu yerel değişken için meta verileri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaed9-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaed9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaed9-115">Requirements</span></span>  
 <span data-ttu-id="eaed9-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaed9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaed9-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaed9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaed9-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaed9-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="eaed9-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="eaed9-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eaed9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaed9-120">See also</span></span>

- [<span data-ttu-id="eaed9-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaed9-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

---
title: "ICorDebugVariableSymbol::GetSlotIndex yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb84e529768e0be44883511bb89703a4c3199df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="a601a-102">ICorDebugVariableSymbol::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="a601a-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="a601a-103">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a601a-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a601a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a601a-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a601a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a601a-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="a601a-106">[out] Yerel değişkenin yuvası dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a601a-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a601a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a601a-107">Return Value</span></span>  
 <span data-ttu-id="a601a-108">`S_OK`başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="a601a-108">`S_OK` if successful.</span></span> <span data-ttu-id="a601a-109">`E_FAIL`değişken bir işlev bağımsız değişkeni ise.</span><span class="sxs-lookup"><span data-stu-id="a601a-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a601a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a601a-110">Remarks</span></span>  
 <span data-ttu-id="a601a-111">Yerel değişken yönetilen yuvası dizini değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="a601a-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a601a-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a601a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a601a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a601a-113">Requirements</span></span>  
 <span data-ttu-id="a601a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a601a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a601a-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a601a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a601a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a601a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a601a-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a601a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a601a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a601a-118">See Also</span></span>  
 [<span data-ttu-id="a601a-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a601a-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="a601a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a601a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

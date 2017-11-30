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
ms.openlocfilehash: d632bc792152afcfc94b51235dc0699fb3efc245
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="459fe-102">ICorDebugVariableSymbol::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="459fe-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="459fe-103">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="459fe-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="459fe-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="459fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="459fe-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="459fe-106">[out] Yerel değişkenin yuvası dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="459fe-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="459fe-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="459fe-107">Return Value</span></span>  
 <span data-ttu-id="459fe-108">`S_OK`başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="459fe-108">`S_OK` if successful.</span></span> <span data-ttu-id="459fe-109">`E_FAIL`değişken bir işlev bağımsız değişkeni ise.</span><span class="sxs-lookup"><span data-stu-id="459fe-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="459fe-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="459fe-110">Remarks</span></span>  
 <span data-ttu-id="459fe-111">Yerel değişken yönetilen yuvası dizini değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="459fe-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="459fe-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="459fe-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="459fe-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="459fe-113">Requirements</span></span>  
 <span data-ttu-id="459fe-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="459fe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="459fe-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="459fe-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="459fe-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="459fe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="459fe-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="459fe-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459fe-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="459fe-118">See Also</span></span>  
 [<span data-ttu-id="459fe-119">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="459fe-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="459fe-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="459fe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: "ICorDebugInstanceFieldSymbol::GetSize yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 364144dcef21e7e9c058cb0317970a273aa8ecac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="34382-102">ICorDebugInstanceFieldSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="34382-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="34382-103">Örnek alanı bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="34382-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34382-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34382-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34382-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34382-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="34382-106">[out] Alanın uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="34382-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34382-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34382-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34382-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34382-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34382-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34382-109">Requirements</span></span>  
 <span data-ttu-id="34382-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34382-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34382-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34382-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34382-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34382-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34382-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34382-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34382-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34382-114">See Also</span></span>  
 [<span data-ttu-id="34382-115">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="34382-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="34382-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34382-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

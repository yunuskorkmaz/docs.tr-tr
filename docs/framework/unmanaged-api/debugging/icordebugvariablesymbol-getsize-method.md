---
title: "ICorDebugVariableSymbol::GetSize yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="87943-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="87943-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="87943-103">Bir değişken boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="87943-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87943-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87943-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87943-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87943-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="87943-106">Değişkeni boyutunu içeren bir 32 bit işaretsiz tamsayıyı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87943-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87943-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87943-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87943-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87943-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87943-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87943-109">Requirements</span></span>  
 <span data-ttu-id="87943-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87943-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87943-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87943-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87943-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87943-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87943-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87943-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87943-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87943-114">See Also</span></span>  
 [<span data-ttu-id="87943-115">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="87943-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="87943-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87943-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

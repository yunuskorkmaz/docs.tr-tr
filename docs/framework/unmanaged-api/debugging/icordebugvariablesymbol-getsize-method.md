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
ms.workload: dotnet
ms.openlocfilehash: 99cba63edd56e0d27d5f558a77ee54ebf2629446
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="46717-102">ICorDebugVariableSymbol::GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="46717-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="46717-103">Bir değişken boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="46717-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46717-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46717-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46717-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46717-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="46717-106">Değişkeni boyutunu içeren bir 32 bit işaretsiz tamsayıyı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46717-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46717-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46717-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46717-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46717-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46717-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46717-109">Requirements</span></span>  
 <span data-ttu-id="46717-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46717-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46717-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46717-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46717-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46717-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46717-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46717-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46717-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46717-114">See Also</span></span>  
 [<span data-ttu-id="46717-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46717-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="46717-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="46717-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

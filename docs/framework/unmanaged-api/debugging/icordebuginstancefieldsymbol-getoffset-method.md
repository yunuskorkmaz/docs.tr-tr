---
title: "ICorDebugInstanceFieldSymbol::GetOffset yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 534e3238a4b20e390c4f2168629e0ba93620f55a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="ad615-102">ICorDebugInstanceFieldSymbol::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad615-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="ad615-103">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="ad615-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad615-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad615-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad615-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad615-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="ad615-106">Bu örnek alanı kendi üst sınıfı uzaklığını bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad615-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad615-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad615-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad615-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ad615-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad615-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad615-109">Requirements</span></span>  
 <span data-ttu-id="ad615-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad615-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad615-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad615-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad615-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad615-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad615-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad615-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad615-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad615-114">See Also</span></span>  
 [<span data-ttu-id="ad615-115">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad615-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="ad615-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad615-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.workload: dotnet
ms.openlocfilehash: 1ab38a19d2bd2d06f2a04d7efafcdad6956ad7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="6a847-102">ICorDebugInstanceFieldSymbol::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a847-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="6a847-103">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="6a847-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a847-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a847-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a847-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a847-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="6a847-106">Bu örnek alanı kendi üst sınıfı uzaklığını bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a847-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a847-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a847-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a847-108">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6a847-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a847-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a847-109">Requirements</span></span>  
 <span data-ttu-id="6a847-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a847-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a847-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a847-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a847-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a847-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a847-113">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a847-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a847-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a847-114">See Also</span></span>  
 [<span data-ttu-id="6a847-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a847-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="6a847-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a847-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

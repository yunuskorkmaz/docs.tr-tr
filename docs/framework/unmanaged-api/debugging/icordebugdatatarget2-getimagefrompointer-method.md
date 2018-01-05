---
title: ICorDebugDataTarget2::GetImageFromPointer Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfe25a90fb2084c1f58eff5b42e24b15decb0163
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="c3363-102">ICorDebugDataTarget2::GetImageFromPointer Metodu</span><span class="sxs-lookup"><span data-stu-id="c3363-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="c3363-103">Bu modüldeki bir adresinden modülü taban adresi ve boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3363-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3363-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3363-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3363-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3363-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c3363-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) bir modüldeki bir adresi temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="c3363-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="c3363-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c3363-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="c3363-108">Modül boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3363-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3363-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3363-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3363-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3363-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3363-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3363-111">Requirements</span></span>  
 <span data-ttu-id="c3363-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3363-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3363-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3363-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3363-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3363-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3363-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3363-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3363-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3363-116">See Also</span></span>  
 [<span data-ttu-id="c3363-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3363-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="c3363-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3363-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

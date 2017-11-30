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
ms.openlocfilehash: e56f65aea12c71145c99a9a195b910ef2876aa09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="f12b1-102">ICorDebugDataTarget2::GetImageFromPointer Metodu</span><span class="sxs-lookup"><span data-stu-id="f12b1-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="f12b1-103">Bu modüldeki bir adresinden modülü taban adresi ve boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f12b1-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f12b1-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f12b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f12b1-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="f12b1-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) bir modüldeki bir adresi temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="f12b1-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="f12b1-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="f12b1-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="f12b1-108">Modül boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f12b1-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f12b1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f12b1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f12b1-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f12b1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12b1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f12b1-111">Requirements</span></span>  
 <span data-ttu-id="f12b1-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12b1-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f12b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f12b1-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f12b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f12b1-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12b1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12b1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f12b1-116">See Also</span></span>  
 [<span data-ttu-id="f12b1-117">Icordebugdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f12b1-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="f12b1-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f12b1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

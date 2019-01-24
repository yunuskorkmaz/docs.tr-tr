---
title: ICorDebugDataTarget2::GetImageFromPointer Metodu
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64affd9b262934316fc904b10f1a9c4a7e7657bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539980"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="51ed8-102">ICorDebugDataTarget2::GetImageFromPointer Metodu</span><span class="sxs-lookup"><span data-stu-id="51ed8-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="51ed8-103">Bu modüldeki bir adresinden modülü temel adres ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="51ed8-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ed8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51ed8-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51ed8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51ed8-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="51ed8-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülünde bir adresi temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="51ed8-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="51ed8-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün taban adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="51ed8-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="51ed8-108">Modül boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51ed8-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51ed8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51ed8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51ed8-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51ed8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ed8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51ed8-111">Requirements</span></span>  
 <span data-ttu-id="51ed8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ed8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ed8-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51ed8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51ed8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51ed8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51ed8-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ed8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ed8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51ed8-116">See also</span></span>
- [<span data-ttu-id="51ed8-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51ed8-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="51ed8-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51ed8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

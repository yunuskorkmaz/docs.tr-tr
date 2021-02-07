---
description: 'Daha fazla bilgi edinin: ICorDebugDataTarget2:: GetImageFromPointer yöntemi'
title: ICorDebugDataTarget2::GetImageFromPointer Yöntemi
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: bcf73fa522072707a7b08d90965fcd38188c2bb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764404"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="971f9-103">ICorDebugDataTarget2::GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="971f9-103">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>

<span data-ttu-id="971f9-104">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="971f9-104">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971f9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="971f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="971f9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="971f9-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="971f9-107">Modül içindeki bir adresi temsil eden [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="971f9-107">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="971f9-108">dışı Modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="971f9-108">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="971f9-109">Modül boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="971f9-109">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="971f9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="971f9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="971f9-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="971f9-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="971f9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="971f9-112">Requirements</span></span>  

 <span data-ttu-id="971f9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="971f9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="971f9-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="971f9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="971f9-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="971f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="971f9-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="971f9-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971f9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="971f9-117">See also</span></span>

- [<span data-ttu-id="971f9-118">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="971f9-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="971f9-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="971f9-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugDataTarget2::GetImageFromPointer Yöntemi
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: f316ddb04cdaad2f528e8fac0a970ca6263ebd8f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976479"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="859e7-102">ICorDebugDataTarget2::GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="859e7-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="859e7-103">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="859e7-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="859e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="859e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="859e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="859e7-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="859e7-106">Modül içindeki bir adresi temsil eden [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="859e7-106">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="859e7-107">dışı Modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="859e7-107">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="859e7-108">Modül boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="859e7-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="859e7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="859e7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="859e7-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="859e7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="859e7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="859e7-111">Requirements</span></span>  
 <span data-ttu-id="859e7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="859e7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="859e7-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="859e7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="859e7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="859e7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="859e7-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="859e7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859e7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="859e7-116">See also</span></span>

- [<span data-ttu-id="859e7-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="859e7-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="859e7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="859e7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

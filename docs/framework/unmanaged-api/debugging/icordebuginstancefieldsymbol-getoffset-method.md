---
title: 'Icordebugınstancefieldsymbol:: GetOffset Yöntemi'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 2d73de46bbb1023f20dd9023076630611c74be5d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724929"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="0d0bb-102">Icordebugınstancefieldsymbol:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d0bb-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="0d0bb-103">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="0d0bb-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0bb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d0bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d0bb-105">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="0d0bb-106">Bu örnek alanın üst sınıfında kaydırılacağı bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d0bb-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0bb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d0bb-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d0bb-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d0bb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d0bb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d0bb-109">Requirements</span></span>  

 <span data-ttu-id="0d0bb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d0bb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d0bb-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d0bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d0bb-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d0bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d0bb-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d0bb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0bb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d0bb-114">See also</span></span>

- [<span data-ttu-id="0d0bb-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d0bb-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="0d0bb-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0d0bb-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

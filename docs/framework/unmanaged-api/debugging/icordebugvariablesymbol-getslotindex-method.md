---
title: ICorDebugVariableSymbol::GetSlotIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09b50af49f8379539773d2000a6c1f8222fee875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563840"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="bfb69-102">ICorDebugVariableSymbol::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfb69-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="bfb69-103">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="bfb69-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfb69-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfb69-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfb69-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="bfb69-106">[out] Yerel değişkenin yuvası dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bfb69-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfb69-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bfb69-107">Return Value</span></span>  
 <span data-ttu-id="bfb69-108">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="bfb69-108">`S_OK` if successful.</span></span> <span data-ttu-id="bfb69-109">`E_FAIL` değişken, işlev bağımsız değişkeni ise.</span><span class="sxs-lookup"><span data-stu-id="bfb69-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfb69-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfb69-110">Remarks</span></span>  
 <span data-ttu-id="bfb69-111">Yerel bir değişken yönetilen yuvası dizinini değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="bfb69-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfb69-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfb69-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb69-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfb69-113">Requirements</span></span>  
 <span data-ttu-id="bfb69-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfb69-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb69-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfb69-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfb69-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfb69-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfb69-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb69-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb69-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfb69-118">See also</span></span>
- [<span data-ttu-id="bfb69-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfb69-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="bfb69-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bfb69-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

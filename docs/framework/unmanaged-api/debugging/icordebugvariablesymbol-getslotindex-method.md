---
title: ICorDebugVariableSymbol::GetSlotIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420628"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="9bcd9-102">ICorDebugVariableSymbol::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bcd9-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="9bcd9-103">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bcd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bcd9-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bcd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bcd9-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="9bcd9-106">[out] Yerel değişkenin yuvası dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bcd9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9bcd9-107">Return Value</span></span>  
 <span data-ttu-id="9bcd9-108">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-108">`S_OK` if successful.</span></span> <span data-ttu-id="9bcd9-109">`E_FAIL` değişken bir işlev bağımsız değişkeni ise.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bcd9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bcd9-110">Remarks</span></span>  
 <span data-ttu-id="9bcd9-111">Yerel değişken yönetilen yuvası dizini değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="9bcd9-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bcd9-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bcd9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bcd9-113">Requirements</span></span>  
 <span data-ttu-id="9bcd9-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bcd9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bcd9-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bcd9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bcd9-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bcd9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bcd9-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bcd9-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bcd9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bcd9-118">See Also</span></span>  
 [<span data-ttu-id="9bcd9-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bcd9-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="9bcd9-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9bcd9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

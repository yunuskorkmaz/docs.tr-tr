---
title: ICorDebugVariableSymbol::GetSlotIndex yöntemi
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d9e30a2baf08f6b7ff530f2fce049d49386a60
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774851"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="e12b6-102">ICorDebugVariableSymbol::GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="e12b6-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="e12b6-103">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e12b6-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e12b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e12b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e12b6-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="e12b6-106">[out] Yerel değişkenin yuvası dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e12b6-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e12b6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e12b6-107">Return Value</span></span>  
 <span data-ttu-id="e12b6-108">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="e12b6-108">`S_OK` if successful.</span></span> <span data-ttu-id="e12b6-109">`E_FAIL` değişken, işlev bağımsız değişkeni ise.</span><span class="sxs-lookup"><span data-stu-id="e12b6-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e12b6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e12b6-110">Remarks</span></span>  
 <span data-ttu-id="e12b6-111">Yerel bir değişken yönetilen yuvası dizinini değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="e12b6-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e12b6-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e12b6-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e12b6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e12b6-113">Requirements</span></span>  
 <span data-ttu-id="e12b6-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e12b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e12b6-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e12b6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e12b6-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e12b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e12b6-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12b6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12b6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e12b6-118">See also</span></span>

- [<span data-ttu-id="e12b6-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e12b6-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="e12b6-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e12b6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

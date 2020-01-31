---
title: 'ICorDebugVariableSymbol:: Getslotındex yöntemi'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790887"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="87c5c-102">ICorDebugVariableSymbol:: Getslotındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="87c5c-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="87c5c-103">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="87c5c-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87c5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87c5c-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="87c5c-106">dışı Yerel değişkenin yuva dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87c5c-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87c5c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87c5c-107">Return Value</span></span>  
 <span data-ttu-id="87c5c-108">başarılı olursa `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="87c5c-108">`S_OK` if successful.</span></span> <span data-ttu-id="87c5c-109">değişken bir işlev bağımsız değişkenidir `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="87c5c-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c5c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87c5c-110">Remarks</span></span>  
 <span data-ttu-id="87c5c-111">Bir yerel değişkenin yönetilen yuva dizini, değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="87c5c-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87c5c-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87c5c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c5c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87c5c-113">Requirements</span></span>  
 <span data-ttu-id="87c5c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87c5c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c5c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87c5c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87c5c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87c5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87c5c-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c5c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c5c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c5c-118">See also</span></span>

- [<span data-ttu-id="87c5c-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87c5c-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="87c5c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87c5c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

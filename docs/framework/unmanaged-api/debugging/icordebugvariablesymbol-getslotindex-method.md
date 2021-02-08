---
description: ': ICorDebugVariableSymbol:: Getslotındex yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugVariableSymbol:: Getslotındex yöntemi'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3b5cba06a5e80ffa323d2e6521e9ec4666f6f5f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790561"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="b6907-103">ICorDebugVariableSymbol:: Getslotındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6907-103">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>

<span data-ttu-id="b6907-104">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="b6907-104">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6907-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6907-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6907-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6907-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="b6907-107">dışı Yerel değişkenin yuva dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6907-107">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6907-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6907-108">Return Value</span></span>  

 <span data-ttu-id="b6907-109">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="b6907-109">`S_OK` if successful.</span></span> <span data-ttu-id="b6907-110">`E_FAIL` değişken bir işlev bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="b6907-110">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6907-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6907-111">Remarks</span></span>  

 <span data-ttu-id="b6907-112">Bir yerel değişkenin yönetilen yuva dizini, değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="b6907-112">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6907-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6907-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6907-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6907-114">Requirements</span></span>  

 <span data-ttu-id="b6907-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6907-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6907-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6907-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6907-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6907-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6907-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6907-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6907-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6907-119">See also</span></span>

- [<span data-ttu-id="b6907-120">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6907-120">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="b6907-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b6907-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

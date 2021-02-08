---
description: ': ICorDebugVariableSymbol:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugVariableSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: f4098bf5e053ab66dd7966d4b665cfad4dee01d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790587"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="0a53c-103">ICorDebugVariableSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a53c-103">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="0a53c-104">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="0a53c-104">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a53c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a53c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a53c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a53c-106">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="0a53c-107">Değişkenin boyutunu içeren 32 bitlik işaretsiz tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0a53c-107">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a53c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a53c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a53c-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a53c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a53c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a53c-110">Requirements</span></span>  

 <span data-ttu-id="0a53c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a53c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a53c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0a53c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a53c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0a53c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a53c-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a53c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a53c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a53c-115">See also</span></span>

- [<span data-ttu-id="0a53c-116">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a53c-116">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="0a53c-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a53c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

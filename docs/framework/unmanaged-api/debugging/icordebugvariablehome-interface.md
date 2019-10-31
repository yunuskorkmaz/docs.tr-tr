---
title: ICorDebugVariableHome Arabirimi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: 306a07450b8ae6d29875ca0cc4679390472e4d1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121036"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="5c453-102">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c453-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="5c453-103">Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c453-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c453-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c453-104">Methods</span></span>  
  
|<span data-ttu-id="5c453-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c453-105">Method</span></span>|<span data-ttu-id="5c453-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c453-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c453-107">GetArgumentIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="5c453-108">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="5c453-109">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="5c453-110">Bu `ICorDebugVariableHome` nesnesini içeren "ICorDebugCode" örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="5c453-111">GetLiveRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="5c453-112">Bu değişkenin canlı olduğu yerel aralığı alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="5c453-113">GetLocationType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="5c453-114">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="5c453-115">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="5c453-116">Bir değişken için temel kaydın konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="5c453-117">GetRegister Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="5c453-118">`VLT_REGISTER`konum türüne sahip bir değişken içeren kaydı alır ve `VLT_REGISTER_RELATIVE`konum türü olan bir değişken için temel kayıt olur.</span><span class="sxs-lookup"><span data-stu-id="5c453-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="5c453-119">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c453-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="5c453-120">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="5c453-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5c453-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c453-121">Example</span></span>  
 <span data-ttu-id="5c453-122">Aşağıdaki kod parçası `pCode4`adlı [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c453-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="5c453-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c453-123">Requirements</span></span>  
 <span data-ttu-id="5c453-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c453-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c453-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c453-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c453-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c453-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c453-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c453-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c453-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c453-128">See also</span></span>

- [<span data-ttu-id="5c453-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c453-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5c453-130">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c453-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)

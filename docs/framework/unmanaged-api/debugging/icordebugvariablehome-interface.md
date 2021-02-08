---
description: 'Daha fazla bilgi edinin: ıcordebugvariablehome arabirimi'
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
ms.openlocfilehash: a1dcc959ba9aeffc0e511dcd2f5bb15f58445139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790639"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="d7743-103">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7743-103">ICorDebugVariableHome Interface</span></span>

<span data-ttu-id="d7743-104">Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d7743-104">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7743-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7743-105">Methods</span></span>  
  
|<span data-ttu-id="d7743-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d7743-106">Method</span></span>|<span data-ttu-id="d7743-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7743-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7743-108">GetArgumentIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-108">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="d7743-109">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="d7743-109">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="d7743-110">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-110">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="d7743-111">Bu nesneyi içeren "ICorDebugCode" örneğini alır `ICorDebugVariableHome` .</span><span class="sxs-lookup"><span data-stu-id="d7743-111">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="d7743-112">GetLiveRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-112">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="d7743-113">Bu değişkenin canlı olduğu yerel aralığı alır.</span><span class="sxs-lookup"><span data-stu-id="d7743-113">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="d7743-114">GetLocationType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-114">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="d7743-115">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d7743-115">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="d7743-116">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-116">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="d7743-117">Bir değişken için temel kaydın konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="d7743-117">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="d7743-118">GetRegister Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-118">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="d7743-119">Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="d7743-119">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="d7743-120">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7743-120">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="d7743-121">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="d7743-121">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7743-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7743-122">Example</span></span>  

 <span data-ttu-id="d7743-123">Aşağıdaki kod parçası adlı [ICorDebugCode4](icordebugcode4-interface.md) nesnesini kullanır `pCode4` .</span><span class="sxs-lookup"><span data-stu-id="d7743-123">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="d7743-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7743-124">Requirements</span></span>  

 <span data-ttu-id="d7743-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7743-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7743-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7743-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7743-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d7743-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7743-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7743-128">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7743-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7743-129">See also</span></span>

- [<span data-ttu-id="d7743-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d7743-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d7743-131">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7743-131">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)

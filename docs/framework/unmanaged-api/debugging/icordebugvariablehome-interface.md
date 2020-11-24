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
ms.openlocfilehash: 089e68278113dfdf509ed848f424ad32baa145ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679552"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="50149-102">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50149-102">ICorDebugVariableHome Interface</span></span>

<span data-ttu-id="50149-103">Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50149-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50149-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50149-104">Methods</span></span>  
  
|<span data-ttu-id="50149-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50149-105">Method</span></span>|<span data-ttu-id="50149-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50149-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50149-107">GetArgumentIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="50149-108">Bir işlev bağımsız değişkeninin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="50149-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="50149-109">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="50149-110">Bu nesneyi içeren "ICorDebugCode" örneğini alır `ICorDebugVariableHome` .</span><span class="sxs-lookup"><span data-stu-id="50149-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="50149-111">GetLiveRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="50149-112">Bu değişkenin canlı olduğu yerel aralığı alır.</span><span class="sxs-lookup"><span data-stu-id="50149-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="50149-113">GetLocationType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="50149-114">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="50149-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="50149-115">GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="50149-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="50149-116">Bir değişken için temel kaydın konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="50149-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="50149-117">GetRegister Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="50149-118">Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="50149-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="50149-119">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50149-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="50149-120">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="50149-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="50149-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="50149-121">Example</span></span>  

 <span data-ttu-id="50149-122">Aşağıdaki kod parçası adlı [ICorDebugCode4](icordebugcode4-interface.md) nesnesini kullanır `pCode4` .</span><span class="sxs-lookup"><span data-stu-id="50149-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="50149-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50149-123">Requirements</span></span>  

 <span data-ttu-id="50149-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50149-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50149-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50149-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50149-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50149-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50149-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50149-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50149-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50149-128">See also</span></span>

- [<span data-ttu-id="50149-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50149-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="50149-130">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50149-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)

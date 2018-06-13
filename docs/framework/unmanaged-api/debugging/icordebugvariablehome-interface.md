---
title: ICorDebugVariableHome arabirimi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422539"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="4402e-102">ICorDebugVariableHome arabirimi</span><span class="sxs-lookup"><span data-stu-id="4402e-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="4402e-103">Yerel bir değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4402e-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4402e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4402e-104">Methods</span></span>  
  
|<span data-ttu-id="4402e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4402e-105">Method</span></span>|<span data-ttu-id="4402e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4402e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4402e-107">GetArgumentIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="4402e-108">Bir işlev bağımsız değişkeni dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="4402e-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="4402e-109">GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="4402e-110">Bu içeren "ICorDebugCode" örneği alır `ICorDebugVariableHome` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4402e-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="4402e-111">GetLiveRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="4402e-112">Bu değişken Canlı yerel aralığı alır.</span><span class="sxs-lookup"><span data-stu-id="4402e-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="4402e-113">GetLocationType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="4402e-114">Değişkenin yerel konum türünü alır.</span><span class="sxs-lookup"><span data-stu-id="4402e-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="4402e-115">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="4402e-116">Uzaklık bir değişken için temel kasadan alır.</span><span class="sxs-lookup"><span data-stu-id="4402e-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="4402e-117">GetRegister Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="4402e-118">Konum türüne sahip bir değişken içeriyor kayıt alır `VLT_REGISTER`ve temel kaydetme konumu türüne sahip bir değişken için `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="4402e-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="4402e-119">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4402e-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="4402e-120">Yönetilen yuvası dizin yerel değişken alır.</span><span class="sxs-lookup"><span data-stu-id="4402e-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4402e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4402e-121">Example</span></span>  
 <span data-ttu-id="4402e-122">Aşağıdaki kod parçası kullanan [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) adlı nesne `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="4402e-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="4402e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4402e-123">Requirements</span></span>  
 <span data-ttu-id="4402e-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4402e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4402e-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4402e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4402e-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4402e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4402e-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4402e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4402e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4402e-128">See Also</span></span>  
 [<span data-ttu-id="4402e-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4402e-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4402e-130">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4402e-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)

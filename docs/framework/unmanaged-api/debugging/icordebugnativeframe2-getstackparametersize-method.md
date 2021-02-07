---
description: 'Daha fazla bilgi edinin: ICorDebugNativeFrame2:: GetStackParameterSize Yöntemi'
title: ICorDebugNativeFrame2::GetStackParameterSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 08a17ced0be75737c1c49aa3f9bb42b13bbe8aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722340"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="8f1fc-103">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f1fc-103">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>

<span data-ttu-id="8f1fc-104">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-104">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f1fc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f1fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f1fc-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="8f1fc-107">dışı Yığındaki parametrelerin birikimli boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-107">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f1fc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f1fc-108">Return Value</span></span>  

 <span data-ttu-id="8f1fc-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8f1fc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f1fc-110">HRESULT</span></span>|<span data-ttu-id="8f1fc-111">Description</span><span class="sxs-lookup"><span data-stu-id="8f1fc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f1fc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f1fc-112">S_OK</span></span>|<span data-ttu-id="8f1fc-113">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-113">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="8f1fc-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8f1fc-114">S_FALSE</span></span>|<span data-ttu-id="8f1fc-115">`GetStackParameterSize` , x86 olmayan bir platformda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-115">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="8f1fc-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f1fc-116">E_FAIL</span></span>|<span data-ttu-id="8f1fc-117">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-117">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="8f1fc-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f1fc-118">E_INVALIDARG</span></span>|<span data-ttu-id="8f1fc-119">`pSize``null`.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-119">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8f1fc-120">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="8f1fc-120">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f1fc-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f1fc-121">Remarks</span></span>  

 <span data-ttu-id="8f1fc-122">[Icordebugstackyürüme](icordebugstackwalk-interface.md) yöntemleri, yığına gönderilen parametrelerin yığın işaretçisini ayarlamadığında.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-122">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="8f1fc-123">Bunun yerine, tarafından döndürülen değeri, `GetStackParameterSize` bir yerel unwinder, parametreler için ayarlanacak şekilde, yığın işaretçisini ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-123">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f1fc-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f1fc-124">Requirements</span></span>  

 <span data-ttu-id="8f1fc-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f1fc-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f1fc-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f1fc-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f1fc-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f1fc-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f1fc-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f1fc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1fc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f1fc-129">See also</span></span>

- [<span data-ttu-id="8f1fc-130">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f1fc-130">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="8f1fc-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8f1fc-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8f1fc-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8f1fc-132">Debugging</span></span>](index.md)

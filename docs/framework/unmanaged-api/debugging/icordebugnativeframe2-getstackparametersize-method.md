---
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
ms.openlocfilehash: 21af3980de9b5a768b6af9a8aca74b693c7ac528
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695503"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="1f080-102">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f080-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>

<span data-ttu-id="1f080-103">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f080-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f080-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1f080-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f080-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f080-105">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="1f080-106">dışı Yığındaki parametrelerin birikimli boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f080-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f080-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f080-107">Return Value</span></span>  

 <span data-ttu-id="1f080-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f080-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1f080-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f080-109">HRESULT</span></span>|<span data-ttu-id="1f080-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f080-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f080-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f080-111">S_OK</span></span>|<span data-ttu-id="1f080-112">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f080-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="1f080-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1f080-113">S_FALSE</span></span>|<span data-ttu-id="1f080-114">`GetStackParameterSize` , x86 olmayan bir platformda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="1f080-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="1f080-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f080-115">E_FAIL</span></span>|<span data-ttu-id="1f080-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="1f080-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="1f080-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1f080-117">E_INVALIDARG</span></span>|<span data-ttu-id="1f080-118">`pSize``null`.</span><span class="sxs-lookup"><span data-stu-id="1f080-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1f080-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="1f080-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f080-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f080-120">Remarks</span></span>  

 <span data-ttu-id="1f080-121">[Icordebugstackyürüme](icordebugstackwalk-interface.md) yöntemleri, yığına gönderilen parametrelerin yığın işaretçisini ayarlamadığında.</span><span class="sxs-lookup"><span data-stu-id="1f080-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="1f080-122">Bunun yerine, tarafından döndürülen değeri, `GetStackParameterSize` bir yerel unwinder, parametreler için ayarlanacak şekilde, yığın işaretçisini ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f080-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f080-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f080-123">Requirements</span></span>  

 <span data-ttu-id="1f080-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f080-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f080-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f080-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f080-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f080-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f080-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f080-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f080-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f080-128">See also</span></span>

- [<span data-ttu-id="1f080-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f080-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="1f080-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1f080-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1f080-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1f080-131">Debugging</span></span>](index.md)

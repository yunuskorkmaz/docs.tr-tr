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
ms.openlocfilehash: b88b3907eb555050de93f35411629b2bd30c7375
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212951"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="2033e-102">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2033e-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="2033e-103">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2033e-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2033e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2033e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="2033e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2033e-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="2033e-106">dışı Yığındaki parametrelerin birikimli boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2033e-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2033e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2033e-107">Return Value</span></span>  
 <span data-ttu-id="2033e-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2033e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2033e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2033e-109">HRESULT</span></span>|<span data-ttu-id="2033e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2033e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2033e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2033e-111">S_OK</span></span>|<span data-ttu-id="2033e-112">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2033e-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="2033e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2033e-113">S_FALSE</span></span>|<span data-ttu-id="2033e-114">`GetStackParameterSize`, x86 olmayan bir platformda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="2033e-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="2033e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2033e-115">E_FAIL</span></span>|<span data-ttu-id="2033e-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="2033e-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="2033e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2033e-117">E_INVALIDARG</span></span>|<span data-ttu-id="2033e-118">`pSize``null`.</span><span class="sxs-lookup"><span data-stu-id="2033e-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2033e-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="2033e-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2033e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2033e-120">Remarks</span></span>  
 <span data-ttu-id="2033e-121">[Icordebugstackyürüme](icordebugstackwalk-interface.md) yöntemleri, yığına gönderilen parametrelerin yığın işaretçisini ayarlamadığında.</span><span class="sxs-lookup"><span data-stu-id="2033e-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="2033e-122">Bunun yerine, tarafından döndürülen değeri, `GetStackParameterSize` bir yerel unwinder, parametreler için ayarlanacak şekilde, yığın işaretçisini ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2033e-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2033e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2033e-123">Requirements</span></span>  
 <span data-ttu-id="2033e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2033e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2033e-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2033e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2033e-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2033e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2033e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2033e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2033e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2033e-128">See also</span></span>

- [<span data-ttu-id="2033e-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2033e-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="2033e-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2033e-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2033e-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2033e-131">Debugging</span></span>](index.md)

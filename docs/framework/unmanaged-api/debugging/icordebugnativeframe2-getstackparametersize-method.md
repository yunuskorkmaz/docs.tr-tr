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
ms.openlocfilehash: ca742ba9e89e1d189cfa38dead314df0d8b4e9d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792769"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="33d3f-102">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33d3f-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="33d3f-103">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="33d3f-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33d3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33d3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="33d3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33d3f-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="33d3f-106">dışı Yığındaki parametrelerin birikimli boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33d3f-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33d3f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33d3f-107">Return Value</span></span>  
 <span data-ttu-id="33d3f-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="33d3f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="33d3f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33d3f-109">HRESULT</span></span>|<span data-ttu-id="33d3f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d3f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33d3f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="33d3f-111">S_OK</span></span>|<span data-ttu-id="33d3f-112">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="33d3f-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="33d3f-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="33d3f-113">S_FALSE</span></span>|<span data-ttu-id="33d3f-114">`GetStackParameterSize`, x86 olmayan bir platformda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="33d3f-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="33d3f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33d3f-115">E_FAIL</span></span>|<span data-ttu-id="33d3f-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="33d3f-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="33d3f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="33d3f-117">E_INVALIDARG</span></span>|<span data-ttu-id="33d3f-118">`pSize` `null`.</span><span class="sxs-lookup"><span data-stu-id="33d3f-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="33d3f-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="33d3f-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33d3f-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33d3f-120">Remarks</span></span>  
 <span data-ttu-id="33d3f-121">[Icordebugstackyürüme](icordebugstackwalk-interface.md) yöntemleri, yığına gönderilen parametrelerin yığın işaretçisini ayarlamadığında.</span><span class="sxs-lookup"><span data-stu-id="33d3f-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="33d3f-122">Bunun yerine, `GetStackParameterSize` tarafından döndürülen değeri bir yerel unwinder çekirdek olarak ayarlamak için kullanabilirsiniz. Bu, parametreleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33d3f-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33d3f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33d3f-123">Requirements</span></span>  
 <span data-ttu-id="33d3f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33d3f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33d3f-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33d3f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33d3f-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="33d3f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33d3f-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33d3f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d3f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33d3f-128">See also</span></span>

- [<span data-ttu-id="33d3f-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33d3f-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="33d3f-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="33d3f-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="33d3f-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="33d3f-131">Debugging</span></span>](index.md)

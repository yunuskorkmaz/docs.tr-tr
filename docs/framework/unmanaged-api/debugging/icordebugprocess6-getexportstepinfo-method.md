---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3c69bbc904f54636e56be6d235d1070b9fecf1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="41277-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="41277-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="41277-103">Yönetilen kod ilerleyebilirsiniz yardımcı olmak için dışarı çalışma zamanı işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41277-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41277-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41277-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41277-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41277-105">Parameters</span></span>  
 <span data-ttu-id="41277-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="41277-106">pszExportName</span></span>  
 <span data-ttu-id="41277-107">[in] PE verme tabloda yazıldığı şekilde bir çalışma zamanı dışarı aktarma işlevini adı.</span><span class="sxs-lookup"><span data-stu-id="41277-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="41277-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="41277-108">invokeKind</span></span>  
 <span data-ttu-id="41277-109">[out] Üye işaretçisi [Cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) dışarı aktarılan işlevi yönetilen kod nasıl çağıracağı açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="41277-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="41277-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="41277-110">invokePurpose</span></span>  
 <span data-ttu-id="41277-111">[out] Üye işaretçisi [Cordebugcodeınvokepurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) neden yönetilen kod verilen işlevi çağırır açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="41277-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41277-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41277-112">Return Value</span></span>  
 <span data-ttu-id="41277-113">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="41277-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="41277-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="41277-114">Return value</span></span>|<span data-ttu-id="41277-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41277-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="41277-116">Yöntem çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="41277-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="41277-117">`pInvokeKind`veya `pInvokePurpose` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="41277-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="41277-118">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="41277-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="41277-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="41277-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41277-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41277-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41277-121">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41277-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41277-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41277-122">Requirements</span></span>  
 <span data-ttu-id="41277-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41277-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41277-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41277-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41277-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41277-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41277-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41277-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41277-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41277-127">See Also</span></span>  
 [<span data-ttu-id="41277-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41277-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="41277-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="41277-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

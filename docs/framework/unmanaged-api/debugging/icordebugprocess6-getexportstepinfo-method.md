---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d0758a8603b7c31844b39c9f3beefea04e0a029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422965"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="74c65-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="74c65-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="74c65-103">Yönetilen kod ilerleyebilirsiniz yardımcı olmak için dışarı çalışma zamanı işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="74c65-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74c65-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74c65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74c65-105">Parameters</span></span>  
 <span data-ttu-id="74c65-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="74c65-106">pszExportName</span></span>  
 <span data-ttu-id="74c65-107">[in] PE verme tabloda yazıldığı şekilde bir çalışma zamanı dışarı aktarma işlevini adı.</span><span class="sxs-lookup"><span data-stu-id="74c65-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="74c65-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="74c65-108">invokeKind</span></span>  
 <span data-ttu-id="74c65-109">[out] Üye işaretçisi [Cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) dışarı aktarılan işlevi yönetilen kod nasıl çağıracağı açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="74c65-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="74c65-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="74c65-110">invokePurpose</span></span>  
 <span data-ttu-id="74c65-111">[out] Üye işaretçisi [Cordebugcodeınvokepurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) neden yönetilen kod verilen işlevi çağırır açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="74c65-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74c65-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74c65-112">Return Value</span></span>  
 <span data-ttu-id="74c65-113">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="74c65-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="74c65-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="74c65-114">Return value</span></span>|<span data-ttu-id="74c65-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74c65-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="74c65-116">Yöntem çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="74c65-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="74c65-117">`pInvokeKind` veya `pInvokePurpose` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="74c65-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="74c65-118">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="74c65-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="74c65-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="74c65-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74c65-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74c65-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74c65-121">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74c65-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c65-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74c65-122">Requirements</span></span>  
 <span data-ttu-id="74c65-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c65-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c65-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74c65-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74c65-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74c65-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74c65-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c65-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c65-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74c65-127">See Also</span></span>  
 [<span data-ttu-id="74c65-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c65-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="74c65-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74c65-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

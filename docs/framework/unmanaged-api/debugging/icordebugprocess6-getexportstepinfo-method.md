---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24c3c46a1f347093061983b9185234cc9959b68d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656147"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="acb6a-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="acb6a-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="acb6a-103">Yönetilen kodu adımlayın yardımcı olmak için çalışma zamanı dışa aktarılan işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="acb6a-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb6a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acb6a-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acb6a-105">Parameters</span></span>  
 <span data-ttu-id="acb6a-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="acb6a-106">pszExportName</span></span>  
 <span data-ttu-id="acb6a-107">[in] PE dışa aktarma tablosunda yazıldığı gibi bir çalışma zamanı dışarı aktarma işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="acb6a-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="acb6a-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="acb6a-108">invokeKind</span></span>  
 <span data-ttu-id="acb6a-109">[out] Üye işaretçisi [Cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) yönetilen kod nasıl verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="acb6a-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="acb6a-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="acb6a-110">invokePurpose</span></span>  
 <span data-ttu-id="acb6a-111">[out] Üye işaretçisi [Cordebugcodeınvokepurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) neden yönetilen kod verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="acb6a-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acb6a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="acb6a-112">Return Value</span></span>  
 <span data-ttu-id="acb6a-113">Yöntem aşağıdaki tabloda listelenen değerler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="acb6a-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="acb6a-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="acb6a-114">Return value</span></span>|<span data-ttu-id="acb6a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb6a-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="acb6a-116">Metot çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="acb6a-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="acb6a-117">`pInvokeKind` veya `pInvokePurpose` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="acb6a-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="acb6a-118">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="acb6a-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="acb6a-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="acb6a-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acb6a-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acb6a-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb6a-121">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acb6a-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb6a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acb6a-122">Requirements</span></span>  
 <span data-ttu-id="acb6a-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb6a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb6a-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acb6a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acb6a-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb6a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb6a-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb6a-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb6a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb6a-127">See also</span></span>
- [<span data-ttu-id="acb6a-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acb6a-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="acb6a-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="acb6a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad094cdcc632abecf3b19cbcbfce24220fedcaf5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736409"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="d8c91-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="d8c91-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="d8c91-103">Yönetilen kodu adımlayın yardımcı olmak için çalışma zamanı dışa aktarılan işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8c91-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8c91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8c91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8c91-105">Parameters</span></span>  
 <span data-ttu-id="d8c91-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="d8c91-106">pszExportName</span></span>  
 <span data-ttu-id="d8c91-107">[in] PE dışa aktarma tablosunda yazıldığı gibi bir çalışma zamanı dışarı aktarma işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="d8c91-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="d8c91-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="d8c91-108">invokeKind</span></span>  
 <span data-ttu-id="d8c91-109">[out] Üye işaretçisi [Cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) yönetilen kod nasıl verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d8c91-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="d8c91-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="d8c91-110">invokePurpose</span></span>  
 <span data-ttu-id="d8c91-111">[out] Üye işaretçisi [Cordebugcodeınvokepurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) neden yönetilen kod verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d8c91-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8c91-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8c91-112">Return Value</span></span>  
 <span data-ttu-id="d8c91-113">Yöntem aşağıdaki tabloda listelenen değerler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d8c91-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="d8c91-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d8c91-114">Return value</span></span>|<span data-ttu-id="d8c91-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8c91-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="d8c91-116">Metot çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d8c91-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="d8c91-117">`pInvokeKind` veya `pInvokePurpose` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="d8c91-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="d8c91-118">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d8c91-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="d8c91-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="d8c91-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c91-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8c91-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8c91-121">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8c91-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c91-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8c91-122">Requirements</span></span>  
 <span data-ttu-id="d8c91-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c91-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c91-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8c91-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8c91-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8c91-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8c91-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8c91-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c91-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8c91-127">See also</span></span>

- [<span data-ttu-id="d8c91-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8c91-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d8c91-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8c91-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

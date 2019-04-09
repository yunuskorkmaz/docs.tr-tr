---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137221"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="b9ed8-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="b9ed8-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="b9ed8-103">Yönetilen kodu adımlayın yardımcı olmak için çalışma zamanı dışa aktarılan işlevleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ed8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9ed8-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ed8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9ed8-105">Parameters</span></span>  
 <span data-ttu-id="b9ed8-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="b9ed8-106">pszExportName</span></span>  
 <span data-ttu-id="b9ed8-107">[in] PE dışa aktarma tablosunda yazıldığı gibi bir çalışma zamanı dışarı aktarma işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="b9ed8-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="b9ed8-108">invokeKind</span></span>  
 <span data-ttu-id="b9ed8-109">[out] Üye işaretçisi [Cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) yönetilen kod nasıl verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="b9ed8-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="b9ed8-110">invokePurpose</span></span>  
 <span data-ttu-id="b9ed8-111">[out] Üye işaretçisi [Cordebugcodeınvokepurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) neden yönetilen kod verilen işlevi çağırır açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9ed8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9ed8-112">Return Value</span></span>  
 <span data-ttu-id="b9ed8-113">Yöntem aşağıdaki tabloda listelenen değerler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="b9ed8-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b9ed8-114">Return value</span></span>|<span data-ttu-id="b9ed8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9ed8-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9ed8-116">Metot çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-116">The method call was successful.</span></span>|  
|`E_POINTER`|`pInvokeKind` <span data-ttu-id="b9ed8-117">veya `pInvokePurpose` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-117">or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="b9ed8-118">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="b9ed8-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9ed8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9ed8-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9ed8-121">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ed8-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9ed8-122">Requirements</span></span>  
 <span data-ttu-id="b9ed8-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ed8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ed8-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9ed8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9ed8-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9ed8-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b9ed8-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b9ed8-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9ed8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9ed8-127">See also</span></span>

- [<span data-ttu-id="b9ed8-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9ed8-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="b9ed8-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b9ed8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18af0dde2d1acc65003558a04789de027bb9209f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967409"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="64094-102">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="64094-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="64094-103">Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64094-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64094-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64094-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64094-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64094-105">Parameters</span></span>  
 <span data-ttu-id="64094-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="64094-106">pszExportName</span></span>  
 <span data-ttu-id="64094-107">'ndaki PE dışarı aktarma tablosunda yazıldığı şekilde bir çalışma zamanı dışa aktarma işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="64094-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="64094-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="64094-108">invokeKind</span></span>  
 <span data-ttu-id="64094-109">dışı İçe aktarılmış işlevin yönetilen kodu nasıl çağıracağına ilişkin [cordebugcodeınvokekind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64094-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="64094-110">ınvokeamaç</span><span class="sxs-lookup"><span data-stu-id="64094-110">invokePurpose</span></span>  
 <span data-ttu-id="64094-111">dışı İçe aktarılmış işlevin neden yönetilen kodu çağıradığına ilişkin bir [Cordebugcodeınvokeamaç](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64094-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64094-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64094-112">Return Value</span></span>  
 <span data-ttu-id="64094-113">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="64094-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="64094-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="64094-114">Return value</span></span>|<span data-ttu-id="64094-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64094-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="64094-116">Yöntem çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="64094-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="64094-117">`pInvokeKind`ya `pInvokePurpose` da **null**.</span><span class="sxs-lookup"><span data-stu-id="64094-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="64094-118">Diğer başarısız `HRESULT` değerler.</span><span class="sxs-lookup"><span data-stu-id="64094-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="64094-119">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="64094-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64094-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64094-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64094-121">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64094-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64094-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64094-122">Requirements</span></span>  
 <span data-ttu-id="64094-123">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64094-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64094-124">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64094-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64094-125">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64094-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64094-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64094-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64094-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64094-127">See also</span></span>

- [<span data-ttu-id="64094-128">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64094-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="64094-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64094-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess6:: GetExportStepInfo yöntemi'
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: e14b5e66d90fb2ece91991b3634fc2ad86fac895
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722015"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="c20b4-103">ICorDebugProcess6::GetExportStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="c20b4-103">ICorDebugProcess6::GetExportStepInfo Method</span></span>

<span data-ttu-id="c20b4-104">Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c20b4-104">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c20b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c20b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c20b4-106">Parameters</span></span>  

 <span data-ttu-id="c20b4-107">pszExportName</span><span class="sxs-lookup"><span data-stu-id="c20b4-107">pszExportName</span></span>  
 <span data-ttu-id="c20b4-108">'ndaki PE dışarı aktarma tablosunda yazıldığı şekilde bir çalışma zamanı dışa aktarma işlevinin adı.</span><span class="sxs-lookup"><span data-stu-id="c20b4-108">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="c20b4-109">invokeKind</span><span class="sxs-lookup"><span data-stu-id="c20b4-109">invokeKind</span></span>  
 <span data-ttu-id="c20b4-110">dışı İçe aktarılmış işlevin yönetilen kodu nasıl çağıracağına ilişkin [cordebugcodeınvokekind](cordebugcodeinvokekind-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c20b4-110">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="c20b4-111">ınvokeamaç</span><span class="sxs-lookup"><span data-stu-id="c20b4-111">invokePurpose</span></span>  
 <span data-ttu-id="c20b4-112">dışı İçe aktarılmış işlevin neden yönetilen kodu çağıradığına ilişkin bir [Cordebugcodeınvokeamaç](cordebugcodeinvokepurpose-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c20b4-112">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c20b4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c20b4-113">Return Value</span></span>  

 <span data-ttu-id="c20b4-114">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="c20b4-114">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="c20b4-115">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="c20b4-115">Return value</span></span>|<span data-ttu-id="c20b4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c20b4-116">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="c20b4-117">Yöntem çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c20b4-117">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="c20b4-118">`pInvokeKind` ya `pInvokePurpose` da **null**.</span><span class="sxs-lookup"><span data-stu-id="c20b4-118">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="c20b4-119">Diğer başarısız `HRESULT` değerler.</span><span class="sxs-lookup"><span data-stu-id="c20b4-119">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="c20b4-120">Uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="c20b4-120">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c20b4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c20b4-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c20b4-122">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c20b4-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c20b4-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c20b4-123">Requirements</span></span>  

 <span data-ttu-id="c20b4-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c20b4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c20b4-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c20b4-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c20b4-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c20b4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c20b4-127">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c20b4-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20b4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c20b4-128">See also</span></span>

- [<span data-ttu-id="c20b4-129">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c20b4-129">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="c20b4-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c20b4-130">Debugging Interfaces</span></span>](debugging-interfaces.md)

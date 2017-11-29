---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d40d1799a7c1572e8213fda3a163fb9a84060f92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="738e5-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="738e5-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="738e5-103">Bir başvuru işaretçi işlemek çöp toplama sahip belirtilen yönetilen nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="738e5-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="738e5-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="738e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="738e5-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="738e5-106">[in] Çöp toplama tanıtıcı sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="738e5-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="738e5-107">Bu değer bir <xref:System.IntPtr> nesne ve kaynağından alınan <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için.</span><span class="sxs-lookup"><span data-stu-id="738e5-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="738e5-108">[out] Bir işaretçi adresine Icordebugreferencevalue nesnenin belirtilen yönetilen nesneye bir başvurusu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="738e5-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="738e5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="738e5-109">Remarks</span></span>  
 <span data-ttu-id="738e5-110">Döndürülen başvuru değeri bir atık toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="738e5-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="738e5-111">Döndürülen başvuru normal bir referans gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="738e5-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="738e5-112">Kod yürütmeyi kesme noktası sonra devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="738e5-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="738e5-113">Hedef nesne ömrü başvuru değeri ömrü tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="738e5-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="738e5-114">`GetReferenceValueFromGCHandle` Yöntemi tanıtıcı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="738e5-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="738e5-115">Bu nedenle, `GetReferenceValueFromGCHandle` yöntemi olası bozulmasına neden olabilir hata ayıklayıcı ve geçersiz bir tanıtıcı aktarılırsa ayıklanacak kodu.</span><span class="sxs-lookup"><span data-stu-id="738e5-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738e5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="738e5-116">Requirements</span></span>  
 <span data-ttu-id="738e5-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="738e5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="738e5-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="738e5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="738e5-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="738e5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="738e5-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="738e5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

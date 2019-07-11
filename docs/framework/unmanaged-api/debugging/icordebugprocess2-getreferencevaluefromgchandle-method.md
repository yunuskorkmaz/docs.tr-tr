---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f38f9a3ebd88e0a5abb7a6bc8cb4026dc7d0f068
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736944"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="39980-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="39980-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="39980-103">Bir başvuru işaretçi, tanıtıcı bir çöp toplama olan belirtilen yönetilen nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="39980-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39980-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39980-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39980-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39980-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="39980-106">[in] Bir çöp toplama tanıtıcı olan yönetilen bir nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="39980-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="39980-107">Bu değer bir <xref:System.IntPtr> nesne ve alınabilir <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne.</span><span class="sxs-lookup"><span data-stu-id="39980-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="39980-108">[out] Bir işaretçi adresine Icordebugreferencevalue nesnenin belirtilen yönetilen nesneye bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39980-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39980-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39980-109">Remarks</span></span>  
 <span data-ttu-id="39980-110">Döndürülen başvuru değeri bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="39980-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="39980-111">Döndürülen başvuru, normal bir başvurusu gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="39980-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="39980-112">Kod yürütmeyi bir kesme noktası sonra devam ettiğinde devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="39980-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="39980-113">Hedef nesnenin ömrünü başvuru değeri ömrünü tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="39980-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39980-114">`GetReferenceValueFromGCHandle` Yöntemi tanıtıcı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="39980-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="39980-115">Bu nedenle, `GetReferenceValueFromGCHandle` yöntemi büyük olasılıkla bozulmasına neden olabilir hem hata ayıklayıcı hem de Geçersiz tanıtıcı iletilmezse ayıklanan kodu.</span><span class="sxs-lookup"><span data-stu-id="39980-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39980-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39980-116">Requirements</span></span>  
 <span data-ttu-id="39980-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39980-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39980-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39980-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39980-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39980-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39980-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39980-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

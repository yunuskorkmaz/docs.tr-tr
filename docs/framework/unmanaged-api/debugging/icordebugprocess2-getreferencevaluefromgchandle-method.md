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
ms.openlocfilehash: a5b9d57aab834ba3ca72a2ea8576ec70cd88eb77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713580"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="93f0f-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="93f0f-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="93f0f-103">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="93f0f-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f0f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="93f0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93f0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93f0f-105">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="93f0f-106">'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93f0f-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="93f0f-107">Bu değer bir <xref:System.IntPtr> nesnedir ve <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için öğesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="93f0f-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="93f0f-108">dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93f0f-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93f0f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93f0f-109">Remarks</span></span>  

 <span data-ttu-id="93f0f-110">Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="93f0f-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="93f0f-111">Döndürülen başvuru normal bir başvuru gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="93f0f-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="93f0f-112">Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="93f0f-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="93f0f-113">Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="93f0f-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93f0f-114">`GetReferenceValueFromGCHandle`Yöntemi tanıtıcıyı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="93f0f-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="93f0f-115">Bu nedenle, `GetReferenceValueFromGCHandle` Yöntem hata ayıklayıcıyı ve geçersiz bir tanıtıcı geçiriliyorsa kodun ayıklanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="93f0f-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f0f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93f0f-116">Requirements</span></span>  

 <span data-ttu-id="93f0f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f0f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f0f-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93f0f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93f0f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="93f0f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f0f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f0f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

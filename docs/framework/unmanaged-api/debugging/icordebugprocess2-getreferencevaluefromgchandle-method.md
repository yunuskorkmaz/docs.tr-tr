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
ms.openlocfilehash: 143eefd557511f80007c88c1678143a885377467
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212990"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="401d4-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="401d4-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="401d4-103">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="401d4-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="401d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="401d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="401d4-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="401d4-106">'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="401d4-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="401d4-107">Bu değer bir <xref:System.IntPtr> nesnedir ve <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için öğesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="401d4-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="401d4-108">dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="401d4-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="401d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="401d4-109">Remarks</span></span>  
 <span data-ttu-id="401d4-110">Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="401d4-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="401d4-111">Döndürülen başvuru normal bir başvuru gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="401d4-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="401d4-112">Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="401d4-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="401d4-113">Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="401d4-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="401d4-114">`GetReferenceValueFromGCHandle`Yöntemi tanıtıcıyı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="401d4-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="401d4-115">Bu nedenle, `GetReferenceValueFromGCHandle` Yöntem hata ayıklayıcıyı ve geçersiz bir tanıtıcı geçiriliyorsa kodun ayıklanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="401d4-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401d4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="401d4-116">Requirements</span></span>  
 <span data-ttu-id="401d4-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401d4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401d4-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="401d4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="401d4-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="401d4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="401d4-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401d4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

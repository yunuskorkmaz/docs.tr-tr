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
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137217"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="16f6d-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="16f6d-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="16f6d-103">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="16f6d-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16f6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16f6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16f6d-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="16f6d-106">'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16f6d-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="16f6d-107">Bu değer bir <xref:System.IntPtr> nesnesidir ve yönetilen nesne için <xref:System.Runtime.InteropServices.GCHandle> elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="16f6d-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="16f6d-108">dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16f6d-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16f6d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16f6d-109">Remarks</span></span>  
 <span data-ttu-id="16f6d-110">Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="16f6d-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="16f6d-111">Döndürülen başvuru normal bir başvuru gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="16f6d-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="16f6d-112">Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="16f6d-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="16f6d-113">Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="16f6d-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16f6d-114">`GetReferenceValueFromGCHandle` yöntemi tanıtıcıyı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="16f6d-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="16f6d-115">Bu nedenle `GetReferenceValueFromGCHandle` yöntemi, hem hata ayıklayıcıyı hem de geçersiz bir tanıtıcı geçirildiğinde hata ayıklanan kodu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="16f6d-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f6d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16f6d-116">Requirements</span></span>  
 <span data-ttu-id="16f6d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16f6d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f6d-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16f6d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16f6d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16f6d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16f6d-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f6d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

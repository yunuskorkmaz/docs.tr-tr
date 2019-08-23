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
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943288"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="98f71-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="98f71-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="98f71-103">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="98f71-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98f71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98f71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98f71-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="98f71-106">'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98f71-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="98f71-107">Bu değer bir <xref:System.IntPtr> nesnedir ve yönetilen nesne <xref:System.Runtime.InteropServices.GCHandle> için öğesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="98f71-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="98f71-108">dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98f71-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98f71-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98f71-109">Remarks</span></span>  
 <span data-ttu-id="98f71-110">Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="98f71-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="98f71-111">Döndürülen başvuru normal bir başvuru gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="98f71-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="98f71-112">Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="98f71-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="98f71-113">Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="98f71-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98f71-114">`GetReferenceValueFromGCHandle` Yöntemi tanıtıcıyı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="98f71-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="98f71-115">Bu nedenle, `GetReferenceValueFromGCHandle` yöntem hata ayıklayıcıyı ve geçersiz bir tanıtıcı geçiriliyorsa kodun ayıklanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="98f71-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98f71-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98f71-116">Requirements</span></span>  
 <span data-ttu-id="98f71-117">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98f71-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98f71-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98f71-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98f71-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98f71-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98f71-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98f71-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: GetReferenceValueFromGCHandle yöntemi'
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
ms.openlocfilehash: 02047dee9116d34a365242f2a532766eb60e1c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650250"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="763f6-103">ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="763f6-103">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="763f6-104">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="763f6-104">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="763f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="763f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="763f6-106">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="763f6-107">'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="763f6-107">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="763f6-108">Bu değer bir <xref:System.IntPtr> nesnedir ve <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için öğesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="763f6-108">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="763f6-109">dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="763f6-109">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="763f6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="763f6-110">Remarks</span></span>  

 <span data-ttu-id="763f6-111">Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="763f6-111">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="763f6-112">Döndürülen başvuru normal bir başvuru gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="763f6-112">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="763f6-113">Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="763f6-113">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="763f6-114">Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="763f6-114">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="763f6-115">`GetReferenceValueFromGCHandle`Yöntemi tanıtıcıyı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="763f6-115">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="763f6-116">Bu nedenle, `GetReferenceValueFromGCHandle` Yöntem hata ayıklayıcıyı ve geçersiz bir tanıtıcı geçiriliyorsa kodun ayıklanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="763f6-116">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763f6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="763f6-117">Requirements</span></span>  

 <span data-ttu-id="763f6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="763f6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="763f6-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="763f6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="763f6-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="763f6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="763f6-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="763f6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

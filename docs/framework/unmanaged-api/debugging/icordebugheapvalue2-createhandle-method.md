---
title: ICorDebugHeapValue2::CreateHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779892"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="3918f-102">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3918f-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="3918f-103">Bu Icordebugheapvalue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türün bir tanıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3918f-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3918f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3918f-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3918f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3918f-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="3918f-106">[in] Oluşturulacak tanıtıcı türü belirtir CorDebugHandleType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="3918f-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="3918f-107">[out] Bu yığın değer için yeni işleyici temsil eden Icordebughandlevalue nesnenin adresini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3918f-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3918f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3918f-108">Remarks</span></span>  
 <span data-ttu-id="3918f-109">Tanıtıcı, yığın değeriyle ilişkili olan uygulama etki alanında oluşturulur ve uygulama etki alanı bellekten alırsa geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3918f-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="3918f-110">Bu işlev için yığını değerin birden çok çağrı birden çok oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3918f-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="3918f-111">Tanıtıcıları çöp toplayıcı performansı etkilediğinden, hata ayıklayıcı kendisini tutamaçlarını (yaklaşık 256) aynı anda etkin olan görece daha az sayıda sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3918f-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3918f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3918f-112">Requirements</span></span>  
 <span data-ttu-id="3918f-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3918f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3918f-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3918f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3918f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3918f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3918f-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3918f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

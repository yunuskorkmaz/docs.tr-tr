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
ms.openlocfilehash: cbc056e9a3cc00178b32dee4011da4403dff508a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212782"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="b9ecd-102">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9ecd-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="b9ecd-103">Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türden bir tanıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ecd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9ecd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ecd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9ecd-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="b9ecd-106">'ndaki Oluşturulacak tanıtıcının türünü belirten Cordebugghandlitype numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="b9ecd-107">dışı Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ıcorıbu Ghandtavalue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9ecd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9ecd-108">Remarks</span></span>  
 <span data-ttu-id="b9ecd-109">Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı kaldırıldığında geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="b9ecd-110">Aynı yığın değeri için bu işleve birden çok çağrı birden çok tanıtıcı oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="b9ecd-111">Tutamaçlar çöp toplayıcısının performansını etkilediği için, hata ayıklayıcı kendisini her seferinde etkin olan görece küçük tanıtıcılara (yaklaşık 256) sınıralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9ecd-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ecd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9ecd-112">Requirements</span></span>  
 <span data-ttu-id="b9ecd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ecd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ecd-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b9ecd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9ecd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b9ecd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9ecd-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ecd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

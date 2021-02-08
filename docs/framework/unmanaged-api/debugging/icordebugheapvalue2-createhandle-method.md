---
description: ': ICorDebugHeapValue2:: CreateHandle yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d93fee71441b9c510d517acb9582b8d1d9ce9e10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803665"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="d1522-103">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1522-103">ICorDebugHeapValue2::CreateHandle Method</span></span>

<span data-ttu-id="d1522-104">Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türden bir tanıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1522-104">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1522-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1522-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1522-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1522-106">Parameters</span></span>  

 `type`  
 <span data-ttu-id="d1522-107">'ndaki Oluşturulacak tanıtıcının türünü belirten Cordebugghandlitype numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="d1522-107">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="d1522-108">dışı Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ıcorıbu Ghandtavalue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1522-108">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1522-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1522-109">Remarks</span></span>  

 <span data-ttu-id="d1522-110">Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı kaldırıldığında geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="d1522-110">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="d1522-111">Aynı yığın değeri için bu işleve birden çok çağrı birden çok tanıtıcı oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="d1522-111">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="d1522-112">Tutamaçlar çöp toplayıcısının performansını etkilediği için, hata ayıklayıcı kendisini her seferinde etkin olan görece küçük tanıtıcılara (yaklaşık 256) sınıralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1522-112">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1522-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1522-113">Requirements</span></span>  

 <span data-ttu-id="d1522-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1522-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1522-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1522-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1522-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d1522-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1522-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1522-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

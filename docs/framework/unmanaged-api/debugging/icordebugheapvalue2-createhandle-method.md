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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178874"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="77b8b-102">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77b8b-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="77b8b-103">Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türde bir tutamaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77b8b-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b8b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77b8b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77b8b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77b8b-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="77b8b-106">[içinde] Oluşturulacak tutamaç türünü belirten CorDebugHandleType numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="77b8b-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="77b8b-107">[çıkış] Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ICorDebugHandleValue nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="77b8b-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77b8b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b8b-108">Remarks</span></span>  
 <span data-ttu-id="77b8b-109">Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı boşaltılırsa geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="77b8b-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="77b8b-110">Aynı yığın değeri için bu işleve yapılan birden çok çağrı birden çok tutamaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77b8b-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="77b8b-111">Tutamaçları çöp toplayıcının performansını etkilediğinden, hata ayıklayıcı nın kendisini bir seferde etkin olan nispeten az sayıda (yaklaşık 256) tutamakla sınırlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77b8b-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77b8b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77b8b-112">Requirements</span></span>  
 <span data-ttu-id="77b8b-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77b8b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b8b-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77b8b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77b8b-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77b8b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77b8b-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77b8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

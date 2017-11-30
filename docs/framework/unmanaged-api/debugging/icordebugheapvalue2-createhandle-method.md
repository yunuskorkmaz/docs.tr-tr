---
title: "ICorDebugHeapValue2::CreateHandle Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7feef9af174a63976729f91b5a0b4967fea55b23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="06cfb-102">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06cfb-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="06cfb-103">Belirtilen tür bu Icordebugheapvalue2 nesnesi tarafından temsil edilen yığın değer için bir tanıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06cfb-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06cfb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06cfb-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06cfb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06cfb-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="06cfb-106">[in] Oluşturulacak tanıtıcı türü belirtir CorDebugHandleType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="06cfb-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="06cfb-107">[out] Bir işaretçi adresine Icordebughandlevalue nesnenin Bu yığın değer için yeni tanıtıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06cfb-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06cfb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06cfb-108">Remarks</span></span>  
 <span data-ttu-id="06cfb-109">Tanıtıcı yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı bellekten alırsa geçersiz hale gelecek.</span><span class="sxs-lookup"><span data-stu-id="06cfb-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="06cfb-110">Bu işlev aynı yığın değeri için birden fazla çağrı birden çok işleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06cfb-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="06cfb-111">Hata ayıklayıcı tanıtıcıları atık toplayıcı performansı etkilediğinden, aynı anda etkin olan tanıtıcıları (yaklaşık 256) görece küçük bir dizi kendisine sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06cfb-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06cfb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06cfb-112">Requirements</span></span>  
 <span data-ttu-id="06cfb-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06cfb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06cfb-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06cfb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06cfb-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06cfb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06cfb-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06cfb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

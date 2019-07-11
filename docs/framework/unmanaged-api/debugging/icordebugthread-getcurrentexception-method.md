---
title: ICorDebugThread::GetCurrentException Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762486"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="093db-102">ICorDebugThread::GetCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="093db-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="093db-103">Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durumu temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="093db-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="093db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="093db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="093db-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="093db-106">[out] Adresine bir işaretçi bir `ICorDebugValue` yönetilen kod tarafından şu anda oluşturulan özel durumu temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="093db-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="093db-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="093db-107">Remarks</span></span>  
 <span data-ttu-id="093db-108">Özel durum nesnesi özel durum oluştu sonuna kadar zamandan sunulacaktır `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="093db-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="093db-109">Icordebugeval yöntemler tarafından gerçekleştirilen bir işlev değerlendirmesi özel durum nesneyi kurulumunu temizleyin ve tamamlanma geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="093db-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="093db-110">Özel durumlar iç içe geçirilemez (örneğin, bir özel durum bir filtre veya bir işlev değerlendirmesi oluşturulursa), olabilir bu nedenle tek bir iş parçacığı üzerinde bekleyen birden çok özel durum.</span><span class="sxs-lookup"><span data-stu-id="093db-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="093db-111">`GetCurrentException` en geçerli özel durumun döndürür.</span><span class="sxs-lookup"><span data-stu-id="093db-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="093db-112">Tür ve özel durum nesnesi özel durum ömrü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="093db-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="093db-113">Örneğin, x türünde bir özel durum oluştuktan sonra ortak dil çalışma zamanı (CLR) bellek taşmasına uğruyor ve bir bellek yetersiz özel durum Yükselt.</span><span class="sxs-lookup"><span data-stu-id="093db-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="093db-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="093db-114">Requirements</span></span>  
 <span data-ttu-id="093db-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="093db-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093db-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="093db-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="093db-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="093db-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="093db-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="093db-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

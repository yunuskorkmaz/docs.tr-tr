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
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133485"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="2f2ef-102">ICorDebugThread::GetCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="2f2ef-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="2f2ef-103">Yönetilen kod tarafından şu anda oluşturulmakta olan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f2ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f2ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f2ef-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="2f2ef-106">dışı Yönetilen kod tarafından şu anda oluşturulan özel durumu temsil eden bir `ICorDebugValue` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f2ef-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f2ef-107">Remarks</span></span>  
 <span data-ttu-id="2f2ef-108">Özel durum nesnesi, `catch` bloğunun sonuna kadar özel durumun oluşturulduğu zamandan itibaren mevcut olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="2f2ef-109">Icoralgıladığında Geval yöntemleri tarafından gerçekleştirilen bir işlev değerlendirmesi, kurulum 'daki özel durum nesnesini temizler ve tamamlanarak geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="2f2ef-110">Özel durumlar iç içe olabilir (örneğin, bir filtrede veya bir işlev değerlendirmesinde bir özel durum oluşturulursa), tek bir iş parçacığında birden çok bekleyen özel durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="2f2ef-111">`GetCurrentException` en güncel özel durumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="2f2ef-112">Özel durum nesnesi ve türü özel durumun ömrü boyunca değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="2f2ef-113">Örneğin, x türü bir özel durum oluşturulduktan sonra ortak dil çalışma zamanı (CLR) belleği tükendiğinden bellek dışı bir özel duruma yükseltebilir.</span><span class="sxs-lookup"><span data-stu-id="2f2ef-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f2ef-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f2ef-114">Requirements</span></span>  
 <span data-ttu-id="2f2ef-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f2ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f2ef-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f2ef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f2ef-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f2ef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f2ef-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f2ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

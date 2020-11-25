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
ms.openlocfilehash: c21be7b062b7e2d4129bafabae004351442ab853
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728062"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="136fa-102">ICorDebugThread::GetCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="136fa-102">ICorDebugThread::GetCurrentException Method</span></span>

<span data-ttu-id="136fa-103">Yönetilen kod tarafından şu anda oluşturulmakta olan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="136fa-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136fa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="136fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="136fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="136fa-105">Parameters</span></span>  

 `ppExceptionObject`  
 <span data-ttu-id="136fa-106">dışı `ICorDebugValue` Yönetilen kod tarafından şu anda oluşturulan özel durumu temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="136fa-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="136fa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="136fa-107">Remarks</span></span>  

 <span data-ttu-id="136fa-108">Özel durum nesnesi, bloğun sonuna kadar özel durumun oluşturulduğu zamandan itibaren mevcut olacaktır `catch` .</span><span class="sxs-lookup"><span data-stu-id="136fa-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="136fa-109">Icoralgıladığında Geval yöntemleri tarafından gerçekleştirilen bir işlev değerlendirmesi, kurulum 'daki özel durum nesnesini temizler ve tamamlanarak geri yükler.</span><span class="sxs-lookup"><span data-stu-id="136fa-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="136fa-110">Özel durumlar iç içe olabilir (örneğin, bir filtrede veya bir işlev değerlendirmesinde bir özel durum oluşturulursa), tek bir iş parçacığında birden çok bekleyen özel durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="136fa-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="136fa-111">`GetCurrentException` en güncel özel durumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="136fa-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="136fa-112">Özel durum nesnesi ve türü özel durumun ömrü boyunca değişebilir.</span><span class="sxs-lookup"><span data-stu-id="136fa-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="136fa-113">Örneğin, x türü bir özel durum oluşturulduktan sonra ortak dil çalışma zamanı (CLR) belleği tükendiğinden bellek dışı bir özel duruma yükseltebilir.</span><span class="sxs-lookup"><span data-stu-id="136fa-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136fa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="136fa-114">Requirements</span></span>  

 <span data-ttu-id="136fa-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="136fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136fa-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="136fa-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="136fa-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="136fa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="136fa-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="136fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

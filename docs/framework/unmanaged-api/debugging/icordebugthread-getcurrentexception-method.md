---
title: ICorDebugThread::GetCurrentException Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="188c8-102">ICorDebugThread::GetCurrentException Metodu</span><span class="sxs-lookup"><span data-stu-id="188c8-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="188c8-103">Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durum temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="188c8-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="188c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="188c8-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="188c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="188c8-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="188c8-106">[out] Adresine bir işaretçi bir `ICorDebugValue` yönetilen kodda şu anda tarafından oluşturulan özel durumu temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="188c8-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="188c8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="188c8-107">Remarks</span></span>  
 <span data-ttu-id="188c8-108">Özel durum nesnesi özel sonuna kadar durum zamandan bulunacağı `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="188c8-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="188c8-109">Icordebugeval yöntemler tarafından yapılır, bir işlev değerlendirmesi kurulumunu özel durum nesnesi çıkışı temizleyin ve tamamlanma geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="188c8-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="188c8-110">Özel durumlar iç içe geçirilemez (örneğin, bir özel filtre veya işlev değerlendirmesi durum değilse), olabilir şekilde tek bir iş parçacığı üzerinde birden fazla bekleyen özel durumu.</span><span class="sxs-lookup"><span data-stu-id="188c8-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="188c8-111">`GetCurrentException`en son istisnası döndürür.</span><span class="sxs-lookup"><span data-stu-id="188c8-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="188c8-112">Özel durum nesnesi ve türü özel kullanım ömrü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="188c8-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="188c8-113">Örneğin, x türünde bir özel durum oluşturulduktan sonra ortak dil çalışma zamanı (CLR) belleğin tükenmek ve bir bellek yetersiz özel durum yükseltin.</span><span class="sxs-lookup"><span data-stu-id="188c8-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="188c8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="188c8-114">Requirements</span></span>  
 <span data-ttu-id="188c8-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="188c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="188c8-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="188c8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="188c8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="188c8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="188c8-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="188c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

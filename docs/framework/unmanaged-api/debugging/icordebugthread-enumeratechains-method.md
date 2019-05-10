---
title: ICorDebugThread::EnumerateChains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f131f7566376d6474f3189d5eb612b30bec2e2b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648432"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="5890c-102">ICorDebugThread::EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5890c-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="5890c-103">Bu Icordebugthread nesnesindeki tüm yığın zincirlerini içeren bir Icordebugchainenum Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5890c-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5890c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5890c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5890c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5890c-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="5890c-106">[out] Adresine bir işaretçi bir `ICorDebugChainEnum` etkin (diğer bir deyişle, en son) halkasını başlayarak, bu iş parçacığındaki tüm yığın numaralandırma veren nesnesi zincir.</span><span class="sxs-lookup"><span data-stu-id="5890c-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5890c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5890c-107">Remarks</span></span>  
 <span data-ttu-id="5890c-108">Yığın zincirinin iş parçacığı için fiziksel çağrı yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5890c-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="5890c-109">Aşağıdaki durumlarda bir yığın zincirinin sınırı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5890c-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="5890c-110">Yönetilmeyen veya yönetilene geçiş.</span><span class="sxs-lookup"><span data-stu-id="5890c-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="5890c-111">Bir içerik anahtarı.</span><span class="sxs-lookup"><span data-stu-id="5890c-111">A context switch.</span></span>  
  
- <span data-ttu-id="5890c-112">Bir hata ayıklayıcı, bir kullanıcı iş parçacığının geçirme.</span><span class="sxs-lookup"><span data-stu-id="5890c-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="5890c-113">En basit durumda tek bir bağlamda yalnızca yönetilen kod çalıştıran iş parçacığı yığın zincirlerini ve iş parçacıkları arasında bire bir iletişimin sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="5890c-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="5890c-114">Bir hata ayıklayıcı, tüm iş parçacıklarının fiziksel çağrı yığınlarını mantıksal çağrı yığınlarını yeniden isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5890c-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="5890c-115">Bu, tüm iş parçacıkları zincirleri çağıran/çağrılan ilişkilerine göre sıralama ve bunları regrouping içerir.</span><span class="sxs-lookup"><span data-stu-id="5890c-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5890c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5890c-116">Requirements</span></span>  
 <span data-ttu-id="5890c-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5890c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5890c-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5890c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5890c-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5890c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5890c-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5890c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

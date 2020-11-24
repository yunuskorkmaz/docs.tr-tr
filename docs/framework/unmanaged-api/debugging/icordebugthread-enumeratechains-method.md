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
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688191"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="05575-102">ICorDebugThread::EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05575-102">ICorDebugThread::EnumerateChains Method</span></span>

<span data-ttu-id="05575-103">Bu ICorDebugThread nesnesindeki tüm yığın zincirlerini içeren bir ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="05575-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05575-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="05575-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05575-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05575-105">Parameters</span></span>  

 `ppChains`  
 <span data-ttu-id="05575-106">dışı `ICorDebugChainEnum` Bu iş parçacığında, etkin (yani en son) zincirden başlayarak tüm yığın zincirlerinin numaralandırılmasına izin veren nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05575-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05575-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05575-107">Remarks</span></span>  

 <span data-ttu-id="05575-108">Yığın zinciri, iş parçacığının fiziksel çağrı yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="05575-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="05575-109">Aşağıdaki koşullar bir yığın zinciri sınırı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="05575-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="05575-110">Yönetilmeyenden yönetilene veya yönetilmeyen bir geçişe.</span><span class="sxs-lookup"><span data-stu-id="05575-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="05575-111">Bir bağlam anahtarı.</span><span class="sxs-lookup"><span data-stu-id="05575-111">A context switch.</span></span>  
  
- <span data-ttu-id="05575-112">Bir kullanıcı iş parçacığını bir hata ayıklayıcı ele geçirme.</span><span class="sxs-lookup"><span data-stu-id="05575-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="05575-113">Tek bir bağlamda tamamen yönetilen kod çalıştıran bir iş parçacığı için basit durumda, iş parçacıkları ve yığın zincirleri arasında bire bir yazışmaya sahip olur.</span><span class="sxs-lookup"><span data-stu-id="05575-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="05575-114">Bir hata ayıklayıcı, tüm iş parçacıklarının fiziksel çağrı yığınlarını mantıksal çağrı yığınlarına yeniden düzenlemek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="05575-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="05575-115">Bu, tüm iş parçacıklarının zincirlerini arayan/çağrılan ilişkilerine göre sıralamayı ve yeniden gruplandırmayı kapsar.</span><span class="sxs-lookup"><span data-stu-id="05575-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05575-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05575-116">Requirements</span></span>  

 <span data-ttu-id="05575-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05575-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05575-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05575-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05575-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05575-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05575-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05575-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

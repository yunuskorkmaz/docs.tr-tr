---
title: "ICorDebugThread::EnumerateChains Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="72397-102">ICorDebugThread::EnumerateChains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72397-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="72397-103">Arabirim işaretçisi bu Icordebugthread nesnesindeki tüm yığın zincirleri içeren bir Icordebugchainenum Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="72397-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72397-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72397-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72397-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72397-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="72397-106">[out] Adresine bir işaretçi bir `ICorDebugChainEnum` tüm yığınının numaralandırması veren nesnesi zincir etkin (diğer bir deyişle, en son) zinciri başlayarak, bu iş parçacığında.</span><span class="sxs-lookup"><span data-stu-id="72397-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72397-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72397-107">Remarks</span></span>  
 <span data-ttu-id="72397-108">Yığın zinciri iş parçacığı için fiziksel çağrı yığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72397-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="72397-109">Aşağıdaki koşullarda bir yığın zinciri sınır oluşturun:</span><span class="sxs-lookup"><span data-stu-id="72397-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="72397-110">Yönetilmeyen veya yönetilen için yönetilmeyen geçişi.</span><span class="sxs-lookup"><span data-stu-id="72397-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="72397-111">Bir içerik anahtarı.</span><span class="sxs-lookup"><span data-stu-id="72397-111">A context switch.</span></span>  
  
-   <span data-ttu-id="72397-112">Bir hata ayıklayıcı, kullanıcı iş parçacığı geçirme.</span><span class="sxs-lookup"><span data-stu-id="72397-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="72397-113">Tamamen yönetilen kod tek bir içerik içinde çalışan iş parçacığı en basit durumda, bir bire yığını zincirlerini ve iş parçacıkları arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="72397-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="72397-114">Tüm iş parçacıklarının fiziksel çağrı yığınları mantıksal çağrısı yığınlar halinde düzenlemek bir hata ayıklayıcısı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72397-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="72397-115">Bu iş parçacıkları zincirleri arayan/Aranan ilişkilerini sıralama ve bunları regrouping içerir.</span><span class="sxs-lookup"><span data-stu-id="72397-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72397-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72397-116">Requirements</span></span>  
 <span data-ttu-id="72397-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72397-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72397-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72397-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72397-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72397-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72397-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72397-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

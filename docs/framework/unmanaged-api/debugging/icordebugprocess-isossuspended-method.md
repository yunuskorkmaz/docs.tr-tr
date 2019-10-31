---
title: ICorDebugProcess::IsOSSuspended Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128764"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="096f3-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="096f3-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="096f3-103">Hata ayıklayıcının bu işlemi durdurmasından kaynaklanan belirtilen iş parçacığının askıya alınıp alınmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="096f3-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="096f3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="096f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="096f3-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="096f3-106">'ndaki Söz konusu iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="096f3-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="096f3-107">dışı Belirtilen iş parçacığı askıya alınmışsa `true` Boole değeri işaretçisi; Aksi halde \*`pbSuspended` `false`.</span><span class="sxs-lookup"><span data-stu-id="096f3-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096f3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="096f3-108">Remarks</span></span>  
 <span data-ttu-id="096f3-109">Hata ayıklayıcının bu işlemi durdurmasının bir sonucu olarak belirtilen iş parçacığı askıya alındığında, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="096f3-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="096f3-110">Hata ayıklayıcı kullanıcı arabirimi (UI), iş parçacığının işletim sistemi (OS) askıya alma sayımını kullanıcıya görüntülerse bu bilgileri hesaba almak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="096f3-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="096f3-111">`IsOSSuspended` yöntemi yalnızca yönetilmeyen hata ayıklama bağlamında anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="096f3-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="096f3-112">Yönetilen hata ayıklama sırasında, iş parçacıkları işletim sistemi tarafından askıya alınmış değil, birlikte askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="096f3-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096f3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="096f3-113">Requirements</span></span>  
 <span data-ttu-id="096f3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="096f3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096f3-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="096f3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="096f3-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="096f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="096f3-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

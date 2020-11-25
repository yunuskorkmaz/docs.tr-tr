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
ms.openlocfilehash: fffa61d8e406162251b0934a9846e5a813422798
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724591"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="31cf9-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31cf9-102">ICorDebugProcess::IsOSSuspended Method</span></span>

<span data-ttu-id="31cf9-103">Hata ayıklayıcının bu işlemi durdurmasından kaynaklanan belirtilen iş parçacığının askıya alınıp alınmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="31cf9-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31cf9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="31cf9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31cf9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31cf9-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="31cf9-106">'ndaki Söz konusu iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="31cf9-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="31cf9-107">dışı `true` Belirtilen iş parçacığı askıya alınmışsa bir Boolean değeri işaretçisi; Aksi halde \* `pbSuspended` `false` .</span><span class="sxs-lookup"><span data-stu-id="31cf9-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31cf9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31cf9-108">Remarks</span></span>  

 <span data-ttu-id="31cf9-109">Hata ayıklayıcının bu işlemi durdurmasının bir sonucu olarak belirtilen iş parçacığı askıya alındığında, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="31cf9-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="31cf9-110">Hata ayıklayıcı kullanıcı arabirimi (UI), iş parçacığının işletim sistemi (OS) askıya alma sayımını kullanıcıya görüntülerse bu bilgileri hesaba almak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="31cf9-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="31cf9-111">`IsOSSuspended`Yöntemi yalnızca yönetilmeyen hata ayıklama bağlamında anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="31cf9-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="31cf9-112">Yönetilen hata ayıklama sırasında, iş parçacıkları işletim sistemi tarafından askıya alınmış değil, birlikte askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="31cf9-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31cf9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31cf9-113">Requirements</span></span>  

 <span data-ttu-id="31cf9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31cf9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31cf9-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31cf9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31cf9-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31cf9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31cf9-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31cf9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

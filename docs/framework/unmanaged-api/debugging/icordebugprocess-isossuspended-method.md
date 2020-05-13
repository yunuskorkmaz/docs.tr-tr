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
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212067"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="f29e4-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f29e4-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="f29e4-103">Hata ayıklayıcının bu işlemi durdurmasından kaynaklanan belirtilen iş parçacığının askıya alınıp alınmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f29e4-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f29e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f29e4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f29e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f29e4-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f29e4-106">'ndaki Söz konusu iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f29e4-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="f29e4-107">dışı `true`Belirtilen iş parçacığı askıya alınmışsa bir Boolean değeri işaretçisi; Aksi halde \* `pbSuspended` `false` .</span><span class="sxs-lookup"><span data-stu-id="f29e4-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f29e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f29e4-108">Remarks</span></span>  
 <span data-ttu-id="f29e4-109">Hata ayıklayıcının bu işlemi durdurmasının bir sonucu olarak belirtilen iş parçacığı askıya alındığında, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="f29e4-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="f29e4-110">Hata ayıklayıcı kullanıcı arabirimi (UI), iş parçacığının işletim sistemi (OS) askıya alma sayımını kullanıcıya görüntülerse bu bilgileri hesaba almak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="f29e4-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="f29e4-111">`IsOSSuspended`Yöntemi yalnızca yönetilmeyen hata ayıklama bağlamında anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f29e4-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="f29e4-112">Yönetilen hata ayıklama sırasında, iş parçacıkları işletim sistemi tarafından askıya alınmış değil, birlikte askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f29e4-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f29e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f29e4-113">Requirements</span></span>  
 <span data-ttu-id="f29e4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f29e4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29e4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f29e4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f29e4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f29e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f29e4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

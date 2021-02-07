---
description: ': ICorDebugProcess:: ısossuspsonlandırılan yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: aa5e438418330d9fee51fcdb56a617421df06904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746778"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="4adf3-103">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4adf3-103">ICorDebugProcess::IsOSSuspended Method</span></span>

<span data-ttu-id="4adf3-104">Hata ayıklayıcının bu işlemi durdurmasından kaynaklanan belirtilen iş parçacığının askıya alınıp alınmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4adf3-104">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adf3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4adf3-105">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4adf3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4adf3-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="4adf3-107">'ndaki Söz konusu iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4adf3-107">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="4adf3-108">dışı `true` Belirtilen iş parçacığı askıya alınmışsa bir Boolean değeri işaretçisi; Aksi halde \* `pbSuspended` `false` .</span><span class="sxs-lookup"><span data-stu-id="4adf3-108">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4adf3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4adf3-109">Remarks</span></span>  

 <span data-ttu-id="4adf3-110">Hata ayıklayıcının bu işlemi durdurmasının bir sonucu olarak belirtilen iş parçacığı askıya alındığında, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="4adf3-110">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="4adf3-111">Hata ayıklayıcı kullanıcı arabirimi (UI), iş parçacığının işletim sistemi (OS) askıya alma sayımını kullanıcıya görüntülerse bu bilgileri hesaba almak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="4adf3-111">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="4adf3-112">`IsOSSuspended`Yöntemi yalnızca yönetilmeyen hata ayıklama bağlamında anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="4adf3-112">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="4adf3-113">Yönetilen hata ayıklama sırasında, iş parçacıkları işletim sistemi tarafından askıya alınmış değil, birlikte askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="4adf3-113">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4adf3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4adf3-114">Requirements</span></span>  

 <span data-ttu-id="4adf3-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4adf3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4adf3-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4adf3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4adf3-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4adf3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4adf3-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adf3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

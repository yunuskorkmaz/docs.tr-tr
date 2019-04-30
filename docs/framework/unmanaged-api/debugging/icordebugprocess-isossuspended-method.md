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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775576"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="828ea-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="828ea-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="828ea-103">Bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak belirtilen iş parçacığını askıya olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="828ea-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="828ea-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="828ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="828ea-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="828ea-106">[in] Söz konusu iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="828ea-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="828ea-107">[out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı çağrıldıysa, aksi takdirde askıya alınmış \*`pbSuspended` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="828ea-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="828ea-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="828ea-108">Remarks</span></span>  
 <span data-ttu-id="828ea-109">Belirtilen iş parçacığı bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="828ea-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="828ea-110">Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülerse bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya alma, kullanıcı iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="828ea-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="828ea-111">`IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında göre mantıklı.</span><span class="sxs-lookup"><span data-stu-id="828ea-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="828ea-112">Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine işletim sistemi askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="828ea-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="828ea-113">Requirements</span></span>  
 <span data-ttu-id="828ea-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="828ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="828ea-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="828ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="828ea-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="828ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="828ea-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="828ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

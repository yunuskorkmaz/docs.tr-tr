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
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755464"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="8e570-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e570-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="8e570-103">Bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak belirtilen iş parçacığını askıya olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8e570-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e570-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e570-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e570-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e570-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8e570-106">[in] Söz konusu iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="8e570-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="8e570-107">[out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı çağrıldıysa, aksi takdirde askıya alınmış \*`pbSuspended` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="8e570-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e570-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e570-108">Remarks</span></span>  
 <span data-ttu-id="8e570-109">Belirtilen iş parçacığı bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="8e570-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="8e570-110">Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülerse bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya alma, kullanıcı iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="8e570-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="8e570-111">`IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında göre mantıklı.</span><span class="sxs-lookup"><span data-stu-id="8e570-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="8e570-112">Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine işletim sistemi askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="8e570-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e570-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e570-113">Requirements</span></span>  
 <span data-ttu-id="8e570-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e570-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e570-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e570-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e570-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e570-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e570-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e570-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

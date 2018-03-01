---
title: "ICorDebugProcess::IsOSSuspended Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="6799e-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6799e-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="6799e-103">Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6799e-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6799e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6799e-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6799e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6799e-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6799e-106">[in] Söz konusu iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="6799e-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="6799e-107">[out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı olması durumunda, aksi askıya alınmış \*`pbSuspended` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="6799e-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6799e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6799e-108">Remarks</span></span>  
 <span data-ttu-id="6799e-109">Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="6799e-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="6799e-110">Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülenirse, bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya kullanıcı için iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="6799e-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="6799e-111">`IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında mantıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6799e-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="6799e-112">Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine OS askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="6799e-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6799e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6799e-113">Requirements</span></span>  
 <span data-ttu-id="6799e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6799e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6799e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6799e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6799e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6799e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6799e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6799e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

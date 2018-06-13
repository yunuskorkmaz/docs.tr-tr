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
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419825"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="e7754-102">ICorDebugProcess::IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7754-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="e7754-103">Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e7754-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7754-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7754-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7754-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7754-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e7754-106">[in] Söz konusu iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7754-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="e7754-107">[out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı olması durumunda, aksi askıya alınmış \*`pbSuspended` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="e7754-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7754-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7754-108">Remarks</span></span>  
 <span data-ttu-id="e7754-109">Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır.</span><span class="sxs-lookup"><span data-stu-id="e7754-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="e7754-110">Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülenirse, bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya kullanıcı için iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7754-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="e7754-111">`IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında mantıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e7754-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="e7754-112">Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine OS askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="e7754-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7754-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7754-113">Requirements</span></span>  
 <span data-ttu-id="e7754-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7754-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7754-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7754-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7754-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7754-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7754-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7754-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

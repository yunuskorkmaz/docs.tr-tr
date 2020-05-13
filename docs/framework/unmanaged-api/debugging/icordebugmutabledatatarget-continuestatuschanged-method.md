---
title: 'Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213315"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="b42ef-102">Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="b42ef-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="b42ef-103">Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b42ef-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b42ef-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b42ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b42ef-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="b42ef-106">İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b42ef-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="b42ef-107">İstenen yeni Devamlılık durumunu temsil eden bir [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="b42ef-107">A [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b42ef-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b42ef-108">Remarks</span></span>  
 <span data-ttu-id="b42ef-109">Hata ayıklayıcı, `ContinueStatusChanged` geçerli hata ayıklama olayının normalde işlenme yönteminden farklı olabilecek bir şekilde işlenmesini gerektiren bir ICorDebug yöntemi çağırdığında yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b42ef-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="b42ef-110">Örneğin, bekleyen bir özel durum varsa ve hata ayıklayıcı özel durumu iptal eden bir işlem isterse ( [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya `FuncEval` ), bu API, özel durumun iptal edilmesini istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b42ef-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42ef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b42ef-111">Requirements</span></span>  
 <span data-ttu-id="b42ef-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b42ef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42ef-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b42ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b42ef-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b42ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b42ef-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42ef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b42ef-116">See also</span></span>

- [<span data-ttu-id="b42ef-117">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b42ef-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="b42ef-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b42ef-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugThread4::HadUnhandledException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791348"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="c41d0-102">ICorDebugThread4::HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c41d0-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="c41d0-103">İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c41d0-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c41d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c41d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c41d0-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="c41d0-106">dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı numaralandırmanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c41d0-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c41d0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c41d0-107">Return Value</span></span>  
 <span data-ttu-id="c41d0-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c41d0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c41d0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c41d0-109">HRESULT</span></span>|<span data-ttu-id="c41d0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c41d0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c41d0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c41d0-111">S_OK</span></span>|<span data-ttu-id="c41d0-112">İş parçacığında oluşturulduktan sonra işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="c41d0-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="c41d0-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c41d0-113">S_FALSE</span></span>|<span data-ttu-id="c41d0-114">İş parçacığında işlenmeyen bir özel durum yoktu.</span><span class="sxs-lookup"><span data-stu-id="c41d0-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c41d0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c41d0-115">Remarks</span></span>  
 <span data-ttu-id="c41d0-116">Bu yöntem, iş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c41d0-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="c41d0-117">İşlenmeyen özel durum geri çağrısının tetiklendiği veya yerel JıT-Attach başlatıldığı zaman, bu yöntemin S_OK döndürmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="c41d0-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="c41d0-118">[ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) yönteminin işlenmemiş özel durumu döndürmeyeceği garantisi yoktur; Ancak, işlenmeyen özel durum geri çağırması alındıktan sonra veya yerel JıT-Attach sonrasında işlem henüz devam ettirilmemişse olur.</span><span class="sxs-lookup"><span data-stu-id="c41d0-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="c41d0-119">Ayrıca, yerel JıT-iliştirme tetiklendiğinde işlenmemiş bir özel durumla birden fazla iş parçacığına sahip olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c41d0-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="c41d0-120">Böyle bir durumda, JıT-Attach ' i tetikleyen özel durumu belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="c41d0-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c41d0-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c41d0-121">Requirements</span></span>  
 <span data-ttu-id="c41d0-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c41d0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c41d0-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c41d0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c41d0-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c41d0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c41d0-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c41d0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41d0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c41d0-126">See also</span></span>

- [<span data-ttu-id="c41d0-127">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c41d0-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="c41d0-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c41d0-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c41d0-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c41d0-129">Debugging</span></span>](index.md)

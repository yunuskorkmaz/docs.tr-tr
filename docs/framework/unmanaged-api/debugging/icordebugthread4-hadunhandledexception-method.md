---
description: 'Daha fazla bilgi edinin: ICorDebugThread4:: HadUnhandledException yöntemi'
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
ms.openlocfilehash: cd0ccdbdd68c37b5fbdbd705da7136e5d36baa60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800935"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="603af-103">ICorDebugThread4::HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="603af-103">ICorDebugThread4::HadUnhandledException Method</span></span>

<span data-ttu-id="603af-104">İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="603af-104">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="603af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="603af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="603af-106">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="603af-107">dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı numaralandırmanın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="603af-107">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="603af-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="603af-108">Return Value</span></span>  

 <span data-ttu-id="603af-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="603af-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="603af-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="603af-110">HRESULT</span></span>|<span data-ttu-id="603af-111">Description</span><span class="sxs-lookup"><span data-stu-id="603af-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="603af-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="603af-112">S_OK</span></span>|<span data-ttu-id="603af-113">İş parçacığında oluşturulduktan sonra işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="603af-113">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="603af-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="603af-114">S_FALSE</span></span>|<span data-ttu-id="603af-115">İş parçacığında işlenmeyen bir özel durum yoktu.</span><span class="sxs-lookup"><span data-stu-id="603af-115">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="603af-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="603af-116">Remarks</span></span>  

 <span data-ttu-id="603af-117">Bu yöntem, iş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="603af-117">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="603af-118">İşlenmeyen özel durum geri çağrısının tetiklendiği veya yerel JıT-Attach başlatıldığı zaman, bu yöntemin S_OK döndürmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="603af-118">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="603af-119">[ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) yönteminin işlenmemiş özel durumu döndürmeyeceği garantisi yoktur; Ancak, işlenmeyen özel durum geri çağırması alındıktan sonra veya yerel JıT-Attach sonrasında işlem henüz devam ettirilmemişse olur.</span><span class="sxs-lookup"><span data-stu-id="603af-119">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="603af-120">Ayrıca, yerel JıT-iliştirme tetiklendiğinde işlenmemiş bir özel durumla birden fazla iş parçacığına sahip olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="603af-120">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="603af-121">Böyle bir durumda, JıT-Attach ' i tetikleyen özel durumu belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="603af-121">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="603af-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="603af-122">Requirements</span></span>  

 <span data-ttu-id="603af-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="603af-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="603af-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="603af-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="603af-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="603af-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="603af-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="603af-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603af-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="603af-127">See also</span></span>

- [<span data-ttu-id="603af-128">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="603af-128">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="603af-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="603af-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="603af-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="603af-130">Debugging</span></span>](index.md)

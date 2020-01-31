---
title: ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: dcb2af2507306b22da14c13a42e4019261c8fa8c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866448"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="bcc9c-102">ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcc9c-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="bcc9c-103">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bcc9c-103">Not implemented.</span></span> <span data-ttu-id="bcc9c-104">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="bcc9c-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcc9c-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="bcc9c-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcc9c-106">Requirements</span></span>  
 <span data-ttu-id="bcc9c-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc9c-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc9c-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bcc9c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcc9c-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bcc9c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc9c-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc9c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc9c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcc9c-111">See also</span></span>

- [<span data-ttu-id="bcc9c-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcc9c-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

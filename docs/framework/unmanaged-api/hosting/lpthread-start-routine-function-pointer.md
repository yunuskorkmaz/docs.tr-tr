---
title: LPTHREAD_START_ROUTINE İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d1837f9f9f11ad34140f50ec41aa6fe8a62160
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119320"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="7117b-102">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7117b-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="7117b-103">Bir iş parçacığının yürütülmeye başlandığını ana bilgisayara bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7117b-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="7117b-104">Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7117b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7117b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7117b-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7117b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7117b-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="7117b-107">[in] Yürütmeyi başlattı kodu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7117b-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7117b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7117b-108">Remarks</span></span>  
 <span data-ttu-id="7117b-109">İşleve `LPTHREAD_START_ROUTINE` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7117b-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7117b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7117b-110">Requirements</span></span>  
 <span data-ttu-id="7117b-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7117b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7117b-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7117b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7117b-113">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="7117b-113">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="7117b-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7117b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7117b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7117b-115">See also</span></span>

- [<span data-ttu-id="7117b-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7117b-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

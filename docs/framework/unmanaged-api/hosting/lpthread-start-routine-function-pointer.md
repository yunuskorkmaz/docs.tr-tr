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
ms.openlocfilehash: a81e78c0a34f766e1598dd27506f62bd3132f348
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490165"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="b9ebf-102">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="b9ebf-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="b9ebf-103">Bir iş parçacığının yürütülmeye başlandığını ana bilgisayara bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b9ebf-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="b9ebf-104">Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b9ebf-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ebf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9ebf-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ebf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9ebf-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="b9ebf-107">[in] Yürütmeyi başlattı kodu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9ebf-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9ebf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9ebf-108">Remarks</span></span>  
 <span data-ttu-id="b9ebf-109">İşleve `LPTHREAD_START_ROUTINE` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b9ebf-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ebf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9ebf-110">Requirements</span></span>  
 <span data-ttu-id="b9ebf-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ebf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ebf-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9ebf-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9ebf-113">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="b9ebf-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="b9ebf-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ebf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ebf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9ebf-115">See also</span></span>

- [<span data-ttu-id="b9ebf-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b9ebf-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

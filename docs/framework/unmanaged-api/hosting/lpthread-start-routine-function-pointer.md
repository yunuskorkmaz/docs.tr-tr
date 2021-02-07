---
description: 'Hakkında daha fazla bilgi edinin: LPTHREAD_START_ROUTINE Işlev Işaretçisi'
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
ms.openlocfilehash: 9f79cffb0b5290031915b453353dd47cb3959970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679816"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="5835a-103">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="5835a-103">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="5835a-104">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5835a-104">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="5835a-105">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5835a-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5835a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5835a-106">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5835a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5835a-107">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="5835a-108">'ndaki Yürütmeyi Başlatan koda yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5835a-108">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5835a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5835a-109">Remarks</span></span>  

 <span data-ttu-id="5835a-110">`LPTHREAD_START_ROUTINE`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="5835a-110">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5835a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5835a-111">Requirements</span></span>  

 <span data-ttu-id="5835a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5835a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5835a-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5835a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5835a-114">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="5835a-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5835a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5835a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5835a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5835a-116">See also</span></span>

- [<span data-ttu-id="5835a-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5835a-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

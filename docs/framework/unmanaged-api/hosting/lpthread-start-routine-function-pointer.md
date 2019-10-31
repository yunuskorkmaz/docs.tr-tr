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
ms.openlocfilehash: c6e0c02af93b9df726202f397bbb2afc306f3b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090876"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="0686a-102">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="0686a-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="0686a-103">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="0686a-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="0686a-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0686a-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0686a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0686a-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0686a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0686a-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="0686a-107">'ndaki Yürütmeyi Başlatan koda yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0686a-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0686a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0686a-108">Remarks</span></span>  
 <span data-ttu-id="0686a-109">`LPTHREAD_START_ROUTINE` işaret eden, bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="0686a-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0686a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0686a-110">Requirements</span></span>  
 <span data-ttu-id="0686a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0686a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0686a-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0686a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0686a-113">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="0686a-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0686a-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0686a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0686a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0686a-115">See also</span></span>

- [<span data-ttu-id="0686a-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0686a-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

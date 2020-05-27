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
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008475"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="d4e42-102">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="d4e42-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="d4e42-103">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="d4e42-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="d4e42-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d4e42-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e42-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d4e42-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e42-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4e42-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="d4e42-107">'ndaki Yürütmeyi Başlatan koda yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4e42-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4e42-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4e42-108">Remarks</span></span>  
 <span data-ttu-id="d4e42-109">`LPTHREAD_START_ROUTINE`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.</span><span class="sxs-lookup"><span data-stu-id="d4e42-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e42-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4e42-110">Requirements</span></span>  
 <span data-ttu-id="d4e42-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4e42-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e42-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4e42-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4e42-113">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="d4e42-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d4e42-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e42-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e42-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e42-115">See also</span></span>

- [<span data-ttu-id="d4e42-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d4e42-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

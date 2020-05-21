---
title: ICLRTask::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 5d6e19fe307373c2920fd60b04bff482b238c5c4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762961"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="ff1f1-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="ff1f1-103">Ortak dil çalışma zamanı 'nın (CLR) geçerli [ICLRTask arabirimi](iclrtask-interface.md) örneği tarafından temsil edilen görevi hemen ve koşulsuz olarak iptal etmek için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1f1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="ff1f1-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ff1f1-105">Return Value</span></span>  
  
|<span data-ttu-id="ff1f1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff1f1-106">HRESULT</span></span>|<span data-ttu-id="ff1f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff1f1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff1f1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff1f1-108">S_OK</span></span>|<span data-ttu-id="ff1f1-109">`RudeAbort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="ff1f1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff1f1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff1f1-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff1f1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff1f1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff1f1-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-113">The call timed out.</span></span>|  
|<span data-ttu-id="ff1f1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff1f1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff1f1-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff1f1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff1f1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff1f1-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff1f1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff1f1-118">E_FAIL</span></span>|<span data-ttu-id="ff1f1-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff1f1-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff1f1-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff1f1-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff1f1-122">Remarks</span></span>  
 <span data-ttu-id="ff1f1-123">Bir ana bilgisayar bir `RudeAbort` görevi hemen iptal etmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="ff1f1-124">Sonlandırıcılar ve özel durum işleme yordamlarının yürütülmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1f1-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff1f1-125">Requirements</span></span>  
 <span data-ttu-id="ff1f1-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff1f1-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff1f1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff1f1-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ff1f1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff1f1-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1f1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1f1-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-130">See also</span></span>

- [<span data-ttu-id="ff1f1-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ff1f1-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ff1f1-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ff1f1-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1f1-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

---
title: ICLRRuntimeHost::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d479e271c2cc4ebf9ea6ff349fd28bff37c3857
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436104"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="3d9ee-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d9ee-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="3d9ee-103">Kod yürütmeyi ortak dil çalışma zamanı tarafından (CLR) durdurur.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d9ee-104">Bu yöntem değil ana bilgisayar kaynakları serbest bırakmak, uygulama etki alanları kaldırma veya iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="3d9ee-105">Bu kaynakları serbest bırakmak için işlemi sonlandırmamız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9ee-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d9ee-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3d9ee-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d9ee-107">Return Value</span></span>  
  
|<span data-ttu-id="3d9ee-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d9ee-108">HRESULT</span></span>|<span data-ttu-id="3d9ee-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d9ee-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d9ee-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d9ee-110">S_OK</span></span>|<span data-ttu-id="3d9ee-111">`Stop` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="3d9ee-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d9ee-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d9ee-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d9ee-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d9ee-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d9ee-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-115">The call timed out.</span></span>|  
|<span data-ttu-id="3d9ee-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d9ee-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d9ee-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d9ee-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d9ee-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d9ee-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d9ee-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d9ee-120">E_FAIL</span></span>|<span data-ttu-id="3d9ee-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d9ee-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d9ee-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d9ee-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d9ee-124">Requirements</span></span>  
 <span data-ttu-id="3d9ee-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d9ee-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9ee-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d9ee-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d9ee-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3d9ee-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d9ee-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9ee-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9ee-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9ee-129">See Also</span></span>  
 [<span data-ttu-id="3d9ee-130">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d9ee-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

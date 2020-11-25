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
ms.openlocfilehash: 50e777bde34eb0122ca537da4b73a5e507ce7a7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728803"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="8f565-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f565-102">ICLRRuntimeHost::Stop Method</span></span>

<span data-ttu-id="8f565-103">Ortak dil çalışma zamanı (CLR) tarafından kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="8f565-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f565-104">Bu yöntem, konağa kaynak yayınlamaz, uygulama etki alanlarını kaldırmaz veya iş parçacıklarını yok eder.</span><span class="sxs-lookup"><span data-stu-id="8f565-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="8f565-105">Bu kaynakları serbest bırakmak için işlemi sonlandıramalısınız.</span><span class="sxs-lookup"><span data-stu-id="8f565-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f565-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f565-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8f565-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f565-107">Return Value</span></span>  
  
|<span data-ttu-id="8f565-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f565-108">HRESULT</span></span>|<span data-ttu-id="8f565-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f565-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f565-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f565-110">S_OK</span></span>|<span data-ttu-id="8f565-111">`Stop` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8f565-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="8f565-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f565-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f565-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8f565-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f565-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f565-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f565-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8f565-115">The call timed out.</span></span>|  
|<span data-ttu-id="8f565-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f565-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f565-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8f565-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f565-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f565-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f565-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8f565-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f565-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f565-120">E_FAIL</span></span>|<span data-ttu-id="8f565-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8f565-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f565-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8f565-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f565-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f565-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f565-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f565-124">Requirements</span></span>  

 <span data-ttu-id="8f565-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f565-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f565-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f565-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f565-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8f565-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f565-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f565-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f565-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f565-129">See also</span></span>

- [<span data-ttu-id="8f565-130">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f565-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

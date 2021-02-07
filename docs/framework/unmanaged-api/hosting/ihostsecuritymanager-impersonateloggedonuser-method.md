---
description: 'Şu konuda daha fazla bilgi edinin: IHostSecurityManager:: ImpersonateLoggedOnUser yöntemi'
title: IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: 7b77e0a163551a48629898b1311fc19ba815aaf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671600"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="41c6f-103">IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41c6f-103">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>

<span data-ttu-id="41c6f-104">Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.</span><span class="sxs-lookup"><span data-stu-id="41c6f-104">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41c6f-105">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41c6f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41c6f-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="41c6f-107">'ndaki Kimliğine bürünülen kullanıcının kimlik bilgilerini temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="41c6f-107">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41c6f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41c6f-108">Return Value</span></span>  
  
|<span data-ttu-id="41c6f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41c6f-109">HRESULT</span></span>|<span data-ttu-id="41c6f-110">Description</span><span class="sxs-lookup"><span data-stu-id="41c6f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41c6f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="41c6f-111">S_OK</span></span>|<span data-ttu-id="41c6f-112">`ImpersonateLoggedOnUser` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="41c6f-112">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="41c6f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41c6f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41c6f-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="41c6f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41c6f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41c6f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41c6f-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="41c6f-116">The call timed out.</span></span>|  
|<span data-ttu-id="41c6f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41c6f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41c6f-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="41c6f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41c6f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41c6f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41c6f-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="41c6f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41c6f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41c6f-121">E_FAIL</span></span>|<span data-ttu-id="41c6f-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="41c6f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41c6f-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="41c6f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41c6f-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="41c6f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c6f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41c6f-125">Remarks</span></span>  

 <span data-ttu-id="41c6f-126">`LogonUser`Geçerli Kullanıcı kimliğinin kimlik bilgileri için bir tanıtıcı almak üzere veya ilgili bir Win32 işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="41c6f-126">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="41c6f-127">`HANDLE`Tür, com uyumlu değildir, diğer bir deyişle, boyutu bir işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="41c6f-127">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="41c6f-128">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41c6f-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c6f-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41c6f-129">Requirements</span></span>  

 <span data-ttu-id="41c6f-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c6f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c6f-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41c6f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41c6f-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="41c6f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41c6f-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c6f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c6f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c6f-134">See also</span></span>

- [<span data-ttu-id="41c6f-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41c6f-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="41c6f-136">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41c6f-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="41c6f-137">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41c6f-137">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)

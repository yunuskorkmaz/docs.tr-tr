---
description: ': IHostSecurityManager:: OpenThreadToken yöntemi hakkında daha fazla bilgi edinin'
title: IHostSecurityManager::OpenThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 9e0273f379f4adcf71396630b367a94c623ae15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671574"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="d7236-103">IHostSecurityManager::OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7236-103">IHostSecurityManager::OpenThreadToken Method</span></span>

<span data-ttu-id="d7236-104">Şu anda yürütülmekte olan iş parçacığıyla ilişkili olan isteğe bağlı erişim belirtecini açar.</span><span class="sxs-lookup"><span data-stu-id="d7236-104">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7236-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7236-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7236-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7236-106">Parameters</span></span>  

 `dwDesiredAccess`  
 <span data-ttu-id="d7236-107">'ndaki İş parçacığı belirtecine istenen erişim türlerini belirten bir erişim değerleri maskesi.</span><span class="sxs-lookup"><span data-stu-id="d7236-107">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="d7236-108">Bu değerler Win32 `OpenThreadToken` işlevinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d7236-108">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="d7236-109">İstenen erişim türleri, izin verilecek veya reddedilecek erişim türlerini belirleyen belirtecin kısıtlı erişim denetim listesine (DACL) göre mutabık kılınmakta.</span><span class="sxs-lookup"><span data-stu-id="d7236-109">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="d7236-110">[in] `true` erişim denetiminin, çağıran iş parçacığı için işlemin güvenlik bağlamı kullanılarak yapılması gerektiğini belirtmek için; `false` erişim denetiminin, çağıran iş parçacığının güvenlik bağlamı kullanılarak gerçekleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d7236-110">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="d7236-111">İş parçacığı bir istemciyi taklit alıyorsa, güvenlik bağlamı bir istemci işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7236-111">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="d7236-112">dışı Yeni açılan erişim belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7236-112">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7236-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d7236-113">Return Value</span></span>  
  
|<span data-ttu-id="d7236-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7236-114">HRESULT</span></span>|<span data-ttu-id="d7236-115">Description</span><span class="sxs-lookup"><span data-stu-id="d7236-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7236-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7236-116">S_OK</span></span>|<span data-ttu-id="d7236-117">`OpenThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d7236-117">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="d7236-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7236-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7236-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d7236-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7236-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7236-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7236-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d7236-121">The call timed out.</span></span>|  
|<span data-ttu-id="d7236-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7236-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7236-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7236-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7236-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7236-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7236-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d7236-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7236-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7236-126">E_FAIL</span></span>|<span data-ttu-id="d7236-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d7236-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7236-128">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d7236-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7236-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7236-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7236-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7236-130">Remarks</span></span>  

 <span data-ttu-id="d7236-131">`IHostSecurityManager::OpenThreadToken` aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, ancak Win32 işlevi çağıranın rastgele bir iş parçacığına bir tutamacı geçmesine izin verdiğinden, `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığıyla ilişkili belirteci açar.</span><span class="sxs-lookup"><span data-stu-id="d7236-131">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="d7236-132">`HANDLE`Tür, com uyumlu değildir, diğer bir deyişle, boyutu işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d7236-132">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="d7236-133">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7236-133">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7236-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7236-134">Requirements</span></span>  

 <span data-ttu-id="d7236-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7236-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7236-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7236-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7236-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d7236-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7236-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7236-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7236-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7236-139">See also</span></span>

- [<span data-ttu-id="d7236-140">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7236-140">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d7236-141">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7236-141">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

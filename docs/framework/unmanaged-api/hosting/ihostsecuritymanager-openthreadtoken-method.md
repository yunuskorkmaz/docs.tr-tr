---
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
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121463"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="3c411-102">IHostSecurityManager::OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c411-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="3c411-103">Şu anda yürütülmekte olan iş parçacığıyla ilişkili olan isteğe bağlı erişim belirtecini açar.</span><span class="sxs-lookup"><span data-stu-id="3c411-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c411-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c411-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c411-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c411-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="3c411-106">'ndaki İş parçacığı belirtecine istenen erişim türlerini belirten bir erişim değerleri maskesi.</span><span class="sxs-lookup"><span data-stu-id="3c411-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="3c411-107">Bu değerler, Win32 `OpenThreadToken` işlevinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3c411-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="3c411-108">İstenen erişim türleri, izin verilecek veya reddedilecek erişim türlerini belirleyen belirtecin kısıtlı erişim denetim listesine (DACL) göre mutabık kılınmakta.</span><span class="sxs-lookup"><span data-stu-id="3c411-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="3c411-109">[in] erişim denetiminin, çağıran iş parçacığı için işlemin güvenlik bağlamı kullanılarak yapılması gerektiğini belirtmek üzere `true`; erişim denetiminin, çağıran iş parçacığının kendisi için güvenlik bağlamı kullanılarak gerçekleştirilmesi gerektiğini belirtmek için `false`.</span><span class="sxs-lookup"><span data-stu-id="3c411-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="3c411-110">İş parçacığı bir istemciyi taklit alıyorsa, güvenlik bağlamı bir istemci işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c411-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="3c411-111">dışı Yeni açılan erişim belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3c411-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c411-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c411-112">Return Value</span></span>  
  
|<span data-ttu-id="3c411-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c411-113">HRESULT</span></span>|<span data-ttu-id="3c411-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c411-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c411-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c411-115">S_OK</span></span>|<span data-ttu-id="3c411-116">`OpenThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3c411-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="3c411-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c411-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c411-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3c411-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c411-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c411-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c411-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3c411-120">The call timed out.</span></span>|  
|<span data-ttu-id="3c411-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c411-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c411-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3c411-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c411-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c411-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c411-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3c411-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c411-125">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="3c411-125">E_FAIL</span></span>|<span data-ttu-id="3c411-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3c411-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c411-127">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3c411-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c411-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c411-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c411-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c411-129">Remarks</span></span>  
 <span data-ttu-id="3c411-130">`IHostSecurityManager::OpenThreadToken`, aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, ancak `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığıyla ilişkili belirteci açtığında, bu, çağıran bir iş parçacığına yönelik bir tutamacı açar.</span><span class="sxs-lookup"><span data-stu-id="3c411-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="3c411-131">`HANDLE` türü, COM uyumlu değildir, diğer bir deyişle, boyutu işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3c411-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="3c411-132">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c411-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c411-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c411-133">Requirements</span></span>  
 <span data-ttu-id="3c411-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c411-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c411-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c411-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c411-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3c411-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c411-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c411-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c411-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c411-138">See also</span></span>

- [<span data-ttu-id="3c411-139">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c411-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3c411-140">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c411-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

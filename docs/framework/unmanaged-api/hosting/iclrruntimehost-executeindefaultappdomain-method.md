---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: ed841d1b2ff346ebef668cbd96a58ddfe466b3b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120443"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="0ac38-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ac38-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="0ac38-103">Belirtilen yönetilen derlemede belirtilen türde belirtilen metodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="0ac38-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ac38-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ac38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ac38-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="0ac38-106">'ndaki Yöntemi çağrılacak olan <xref:System.Type> tanımlayan <xref:System.Reflection.Assembly> yolu.</span><span class="sxs-lookup"><span data-stu-id="0ac38-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="0ac38-107">'ndaki Çağrılacak yöntemi tanımlayan <xref:System.Type> adı.</span><span class="sxs-lookup"><span data-stu-id="0ac38-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="0ac38-108">'ndaki Çağrılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="0ac38-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="0ac38-109">'ndaki Yönteme geçirilecek dize parametresi.</span><span class="sxs-lookup"><span data-stu-id="0ac38-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="0ac38-110">dışı Çağrılan yöntem tarafından döndürülen tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="0ac38-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ac38-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ac38-111">Return Value</span></span>  
  
|<span data-ttu-id="0ac38-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ac38-112">HRESULT</span></span>|<span data-ttu-id="0ac38-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ac38-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ac38-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ac38-114">S_OK</span></span>|<span data-ttu-id="0ac38-115">`ExecuteInDefaultAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ac38-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="0ac38-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ac38-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ac38-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ac38-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ac38-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ac38-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ac38-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ac38-119">The call timed out.</span></span>|  
|<span data-ttu-id="0ac38-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ac38-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ac38-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ac38-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ac38-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ac38-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ac38-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0ac38-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ac38-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="0ac38-124">E_FAIL</span></span>|<span data-ttu-id="0ac38-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ac38-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ac38-126">Bir yöntem E_FAıL döndürürse, CRL artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ac38-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="0ac38-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ac38-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ac38-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ac38-128">Remarks</span></span>  
 <span data-ttu-id="0ac38-129">Çağrılan yöntem aşağıdaki imzaya sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="0ac38-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="0ac38-130">`pwzMethodName` çağrılan yöntemin adını temsil eder ve `pwzArgument`, bu yönteme parametre olarak geçirilen dize değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ac38-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="0ac38-131">HRESULT değeri S_OK olarak ayarlandıysa, `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0ac38-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="0ac38-132">Aksi takdirde, `pReturnValue` ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="0ac38-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ac38-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ac38-133">Requirements</span></span>  
 <span data-ttu-id="0ac38-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ac38-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ac38-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ac38-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ac38-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0ac38-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ac38-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ac38-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac38-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac38-138">See also</span></span>

- [<span data-ttu-id="0ac38-139">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ac38-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

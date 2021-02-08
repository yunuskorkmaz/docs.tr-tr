---
description: ': ICLRRuntimeHost:: ExecuteInDefaultAppDomain yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0fae9be69cf67da252dcdb423432ec922c0b00ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785145"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="d3918-103">ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3918-103">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>

<span data-ttu-id="d3918-104">Belirtilen yönetilen derlemede belirtilen türde belirtilen metodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="d3918-104">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3918-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3918-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3918-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3918-106">Parameters</span></span>  

 `pwzAssemblyPath`  
 <span data-ttu-id="d3918-107">'ndaki <xref:System.Reflection.Assembly> Yöntemi çağrılacak öğesini tanımlayan öğesine yolu <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="d3918-107">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="d3918-108">'ndaki <xref:System.Type> Çağrılacak yöntemi tanımlayan öğesinin adı.</span><span class="sxs-lookup"><span data-stu-id="d3918-108">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="d3918-109">'ndaki Çağrılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="d3918-109">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="d3918-110">'ndaki Yönteme geçirilecek dize parametresi.</span><span class="sxs-lookup"><span data-stu-id="d3918-110">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="d3918-111">dışı Çağrılan yöntem tarafından döndürülen tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="d3918-111">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3918-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d3918-112">Return Value</span></span>  
  
|<span data-ttu-id="d3918-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3918-113">HRESULT</span></span>|<span data-ttu-id="d3918-114">Description</span><span class="sxs-lookup"><span data-stu-id="d3918-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3918-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3918-115">S_OK</span></span>|<span data-ttu-id="d3918-116">`ExecuteInDefaultAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d3918-116">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="d3918-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3918-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3918-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d3918-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3918-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3918-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3918-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d3918-120">The call timed out.</span></span>|  
|<span data-ttu-id="d3918-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3918-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3918-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d3918-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3918-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3918-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3918-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d3918-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3918-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3918-125">E_FAIL</span></span>|<span data-ttu-id="d3918-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d3918-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3918-127">Bir yöntem E_FAIL döndürürse, CRL artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d3918-127">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="d3918-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3918-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3918-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3918-129">Remarks</span></span>  

 <span data-ttu-id="d3918-130">Çağrılan yöntem aşağıdaki imzaya sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d3918-130">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="d3918-131">, `pwzMethodName` çağrılan yöntemin adını temsil eder ve `pwzArgument` Bu yönteme parametre olarak geçirilen dize değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d3918-131">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="d3918-132">HRESULT değeri S_OK olarak ayarlandıysa, `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d3918-132">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="d3918-133">Aksi takdirde, `pReturnValue` ayarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d3918-133">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3918-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3918-134">Requirements</span></span>  

 <span data-ttu-id="d3918-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3918-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3918-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3918-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3918-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d3918-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3918-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3918-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3918-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3918-139">See also</span></span>

- [<span data-ttu-id="d3918-140">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3918-140">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

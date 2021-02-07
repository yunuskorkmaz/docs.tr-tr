---
description: ': ICLRRuntimeHost:: GetCLRControl Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeHost::GetCLRControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 832ae03c0126f0c08afa9b5c0312a636ec1de294
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753945"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="91ab5-103">ICLRRuntimeHost::GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91ab5-103">ICLRRuntimeHost::GetCLRControl Method</span></span>

<span data-ttu-id="91ab5-104">Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl arabirimi](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="91ab5-104">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ab5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91ab5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ab5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91ab5-106">Parameters</span></span>  

 `pCLRControl`  
 <span data-ttu-id="91ab5-107">dışı Ana bilgisayarların CLR 'nin ek yönlerini yapılandırmasını sağlayan [ICLRControl arabirimi](iclrcontrol-interface.md) türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="91ab5-107">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91ab5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91ab5-108">Return Value</span></span>  
  
|<span data-ttu-id="91ab5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91ab5-109">HRESULT</span></span>|<span data-ttu-id="91ab5-110">Description</span><span class="sxs-lookup"><span data-stu-id="91ab5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91ab5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91ab5-111">S_OK</span></span>|<span data-ttu-id="91ab5-112">`GetCLRControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="91ab5-112">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="91ab5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91ab5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91ab5-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="91ab5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91ab5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91ab5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91ab5-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="91ab5-116">The call timed out.</span></span>|  
|<span data-ttu-id="91ab5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91ab5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91ab5-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="91ab5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91ab5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91ab5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91ab5-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="91ab5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91ab5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91ab5-121">E_FAIL</span></span>|<span data-ttu-id="91ab5-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="91ab5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91ab5-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="91ab5-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91ab5-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="91ab5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91ab5-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="91ab5-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="91ab5-126">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="91ab5-126">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91ab5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91ab5-127">Remarks</span></span>  

 <span data-ttu-id="91ab5-128">`ICLRControl` Konağın yönetici türlerinden birine bir arabirim işaretçisi almasını sağlayan [GetCLRManager Yöntemi](iclrcontrol-getclrmanager-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91ab5-128">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ab5-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91ab5-129">Requirements</span></span>  

 <span data-ttu-id="91ab5-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ab5-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ab5-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91ab5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91ab5-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="91ab5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91ab5-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ab5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ab5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ab5-134">See also</span></span>

- [<span data-ttu-id="91ab5-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ab5-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="91ab5-136">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ab5-136">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

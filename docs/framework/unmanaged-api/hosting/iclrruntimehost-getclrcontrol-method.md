---
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
ms.openlocfilehash: 68bcdc33e34075cc5876ee721ef57282cdaa6e86
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703690"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="aa6c1-102">ICLRRuntimeHost::GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa6c1-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="aa6c1-103">Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl arabirimi](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-103">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6c1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aa6c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa6c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa6c1-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="aa6c1-106">dışı Ana bilgisayarların CLR 'nin ek yönlerini yapılandırmasını sağlayan [ICLRControl arabirimi](iclrcontrol-interface.md) türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-106">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa6c1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa6c1-107">Return Value</span></span>  
  
|<span data-ttu-id="aa6c1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa6c1-108">HRESULT</span></span>|<span data-ttu-id="aa6c1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa6c1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa6c1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa6c1-110">S_OK</span></span>|<span data-ttu-id="aa6c1-111">`GetCLRControl`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="aa6c1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa6c1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa6c1-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa6c1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa6c1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa6c1-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-115">The call timed out.</span></span>|  
|<span data-ttu-id="aa6c1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa6c1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa6c1-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa6c1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa6c1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa6c1-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa6c1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa6c1-120">E_FAIL</span></span>|<span data-ttu-id="aa6c1-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa6c1-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa6c1-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa6c1-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="aa6c1-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="aa6c1-125">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa6c1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa6c1-126">Remarks</span></span>  
 <span data-ttu-id="aa6c1-127">`ICLRControl`Konağın yönetici türlerinden birine bir arabirim işaretçisi almasını sağlayan [GetCLRManager Yöntemi](iclrcontrol-getclrmanager-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-127">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa6c1-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa6c1-128">Requirements</span></span>  
 <span data-ttu-id="aa6c1-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa6c1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa6c1-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa6c1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa6c1-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aa6c1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa6c1-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6c1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6c1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa6c1-133">See also</span></span>

- [<span data-ttu-id="aa6c1-134">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa6c1-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="aa6c1-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa6c1-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

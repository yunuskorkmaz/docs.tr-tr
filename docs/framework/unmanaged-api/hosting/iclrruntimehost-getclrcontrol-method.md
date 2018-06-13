---
title: ICLRRuntimeHost::GetCLRControl Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86858d5fe5bf9ac07a91e810599c27a479141f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435061"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="b34ab-102">ICLRRuntimeHost::GetCLRControl Metodu</span><span class="sxs-lookup"><span data-stu-id="b34ab-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="b34ab-103">Arabirim işaretçisi türü alır [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b34ab-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b34ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b34ab-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b34ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b34ab-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="b34ab-106">[out] Arabirim işaretçisi türü [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) CLR ek yönlerini yapılandırmak ana bilgisayarları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34ab-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b34ab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b34ab-107">Return Value</span></span>  
  
|<span data-ttu-id="b34ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b34ab-108">HRESULT</span></span>|<span data-ttu-id="b34ab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b34ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b34ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b34ab-110">S_OK</span></span>|<span data-ttu-id="b34ab-111">`GetCLRControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b34ab-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="b34ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b34ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b34ab-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b34ab-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b34ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b34ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b34ab-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b34ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="b34ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b34ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b34ab-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="b34ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b34ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b34ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b34ab-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="b34ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b34ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b34ab-120">E_FAIL</span></span>|<span data-ttu-id="b34ab-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b34ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b34ab-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b34ab-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b34ab-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b34ab-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b34ab-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b34ab-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="b34ab-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b34ab-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b34ab-126">Remarks</span></span>  
 <span data-ttu-id="b34ab-127">`ICLRControl` sağlar [GetCLRManager yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) Yöneticisi türden biri için bir arabirim işaretçisi almak için konağı etkinleştirir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b34ab-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b34ab-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b34ab-128">Requirements</span></span>  
 <span data-ttu-id="b34ab-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b34ab-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b34ab-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b34ab-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b34ab-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b34ab-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b34ab-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b34ab-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34ab-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b34ab-133">See Also</span></span>  
 [<span data-ttu-id="b34ab-134">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b34ab-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b34ab-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b34ab-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

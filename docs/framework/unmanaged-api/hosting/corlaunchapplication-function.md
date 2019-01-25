---
title: CorLaunchApplication İşlevi
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f2a05009caed7bef6da9edee57a4a54b876b18f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580999"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="5d89f-102">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="5d89f-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="5d89f-103">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolunda uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="5d89f-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="5d89f-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d89f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d89f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d89f-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d89f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d89f-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="5d89f-107">[in] Değerini [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) uygulamayı başlatmadan konak türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="5d89f-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="5d89f-108">[in] Başlatılan uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="5d89f-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="5d89f-109">[in] Uygulama için bildirim yolları sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d89f-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="5d89f-110">[in] Her biri bildirim başlatılmayı uygulama için bir yol belirtir bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="5d89f-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="5d89f-111">[in] Başlatılan uygulama için etkinleştirme veri öğesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d89f-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="5d89f-112">[in] Her biri bir etkinleştirme veri öğesi başlatılmayı uygulama için olan bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="5d89f-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="5d89f-113">[out] Uygulama yüklendi işlemi hakkında bilgi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d89f-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d89f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d89f-114">Requirements</span></span>  
 <span data-ttu-id="5d89f-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d89f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d89f-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d89f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d89f-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d89f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d89f-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d89f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d89f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d89f-119">See also</span></span>
- [<span data-ttu-id="5d89f-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5d89f-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

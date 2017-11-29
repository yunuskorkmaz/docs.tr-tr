---
title: "CorLaunchApplication İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6246ab600438e2237dcbe531d9d7641c0897d81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="be881-102">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="be881-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="be881-103">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="be881-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="be881-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be881-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be881-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be881-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="be881-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be881-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="be881-107">[in] Değerini [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) numaralandırma Uygulama başlatılmadan ana bilgisayar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="be881-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="be881-108">[in] Başlatılır uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="be881-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="be881-109">[in] Uygulama için bildirim yolları sayısı.</span><span class="sxs-lookup"><span data-stu-id="be881-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="be881-110">[in] Her biri başlatılır uygulama için bir bildirim yolunu belirtir, bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="be881-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="be881-111">[in] Başlatılır uygulama için etkinleştirme veri öğesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="be881-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="be881-112">[in] Her biri başlatılır uygulama için bir etkinleştirme veri öğesi olan bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="be881-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="be881-113">[out] Uygulama yüklendi işlemi hakkında bilgi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be881-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be881-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be881-114">Requirements</span></span>  
 <span data-ttu-id="be881-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be881-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be881-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be881-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be881-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be881-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be881-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be881-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be881-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be881-119">See Also</span></span>  
 [<span data-ttu-id="be881-120">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="be881-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

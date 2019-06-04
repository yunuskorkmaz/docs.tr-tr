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
ms.openlocfilehash: 64527221e81569bf08a3cfd34a66681725755a55
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490543"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="26401-102">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="26401-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="26401-103">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolunda uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="26401-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="26401-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="26401-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26401-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26401-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="26401-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26401-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="26401-107">[in] Değerini [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) uygulamayı başlatmadan konak türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="26401-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="26401-108">[in] Başlatılan uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="26401-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="26401-109">[in] Uygulama için bildirim yolları sayısı.</span><span class="sxs-lookup"><span data-stu-id="26401-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="26401-110">[in] Her biri bildirim başlatılmayı uygulama için bir yol belirtir bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="26401-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="26401-111">[in] Başlatılan uygulama için etkinleştirme veri öğesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="26401-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="26401-112">[in] Her biri bir etkinleştirme veri öğesi başlatılmayı uygulama için olan bir dizi dizeleri.</span><span class="sxs-lookup"><span data-stu-id="26401-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="26401-113">[out] Uygulama yüklendi işlemi hakkında bilgi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26401-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26401-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26401-114">Requirements</span></span>  
 <span data-ttu-id="26401-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26401-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26401-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26401-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26401-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26401-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26401-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26401-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26401-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26401-119">See also</span></span>

- [<span data-ttu-id="26401-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="26401-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

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
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136942"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="663c9-102">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="663c9-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="663c9-103">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="663c9-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="663c9-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="663c9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="663c9-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="663c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="663c9-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="663c9-107">'ndaki Uygulamayı başlatan konak türünü belirten [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="663c9-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="663c9-108">'ndaki Başlatılmakta olan uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="663c9-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="663c9-109">'ndaki Uygulamanın bildirim yollarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="663c9-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="663c9-110">'ndaki Her biri, başlatılmakta olan uygulama için bir bildirimin yolunu belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="663c9-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="663c9-111">'ndaki Başlatılmakta olan uygulama için etkinleştirme verisi öğelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="663c9-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="663c9-112">'ndaki Her biri, başlatılmakta olan uygulama için bir etkinleştirme verileri öğesi olan dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="663c9-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="663c9-113">dışı Uygulamanın yüklendiği işlem hakkındaki bilgilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="663c9-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="663c9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="663c9-114">Requirements</span></span>  
 <span data-ttu-id="663c9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="663c9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="663c9-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="663c9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="663c9-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="663c9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="663c9-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="663c9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663c9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663c9-119">See also</span></span>

- [<span data-ttu-id="663c9-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="663c9-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

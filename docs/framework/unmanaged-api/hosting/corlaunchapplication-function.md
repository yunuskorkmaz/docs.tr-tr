---
description: 'Daha fazla bilgi edinin: CorLaunchApplication Işlevi'
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
ms.openlocfilehash: 89f1f37ddde69fb5ecc24fd9dfd0d0c27d5fac40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716958"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="4e26f-103">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="4e26f-103">CorLaunchApplication Function</span></span>

<span data-ttu-id="4e26f-104">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="4e26f-104">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="4e26f-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="4e26f-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e26f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e26f-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e26f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e26f-107">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="4e26f-108">'ndaki Uygulamayı başlatan konak türünü belirten [HOST_TYPE](host-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="4e26f-108">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="4e26f-109">'ndaki Başlatılmakta olan uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="4e26f-109">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="4e26f-110">'ndaki Uygulamanın bildirim yollarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="4e26f-110">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="4e26f-111">'ndaki Her biri, başlatılmakta olan uygulama için bir bildirimin yolunu belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="4e26f-111">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="4e26f-112">'ndaki Başlatılmakta olan uygulama için etkinleştirme verisi öğelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="4e26f-112">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="4e26f-113">'ndaki Her biri, başlatılmakta olan uygulama için bir etkinleştirme verileri öğesi olan dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="4e26f-113">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="4e26f-114">dışı Uygulamanın yüklendiği işlem hakkındaki bilgilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e26f-114">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e26f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e26f-115">Requirements</span></span>  

 <span data-ttu-id="4e26f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e26f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e26f-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e26f-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e26f-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e26f-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e26f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e26f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e26f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e26f-120">See also</span></span>

- [<span data-ttu-id="4e26f-121">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4e26f-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

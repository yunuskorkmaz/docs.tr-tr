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
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704077"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="faf2d-102">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="faf2d-102">CorLaunchApplication Function</span></span>

<span data-ttu-id="faf2d-103">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="faf2d-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="faf2d-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="faf2d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf2d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="faf2d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="faf2d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faf2d-106">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="faf2d-107">'ndaki Uygulamayı başlatan konak türünü belirten [HOST_TYPE](host-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="faf2d-107">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="faf2d-108">'ndaki Başlatılmakta olan uygulamanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="faf2d-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="faf2d-109">'ndaki Uygulamanın bildirim yollarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="faf2d-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="faf2d-110">'ndaki Her biri, başlatılmakta olan uygulama için bir bildirimin yolunu belirten dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="faf2d-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="faf2d-111">'ndaki Başlatılmakta olan uygulama için etkinleştirme verisi öğelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="faf2d-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="faf2d-112">'ndaki Her biri, başlatılmakta olan uygulama için bir etkinleştirme verileri öğesi olan dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="faf2d-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="faf2d-113">dışı Uygulamanın yüklendiği işlem hakkındaki bilgilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="faf2d-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf2d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faf2d-114">Requirements</span></span>  

 <span data-ttu-id="faf2d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf2d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf2d-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="faf2d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faf2d-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="faf2d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faf2d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf2d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf2d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faf2d-119">See also</span></span>

- [<span data-ttu-id="faf2d-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="faf2d-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
